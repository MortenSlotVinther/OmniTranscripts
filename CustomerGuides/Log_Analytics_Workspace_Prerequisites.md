# Azure Log Analytics Workspace Prerequisites for OmniGaze

## Overview
This document outlines the prerequisites and configuration requirements for Azure Log Analytics workspace to ensure optimal data collection and integration with OmniGaze. Proper configuration of these tables is essential for comprehensive infrastructure monitoring, application discovery, and performance analysis.

## Required Log Analytics Tables

### 1. VMComputer Table (Essential)
The VMComputer table contains inventory data for all monitored servers and is fundamental for asset discovery.

#### Prerequisites:
- **Azure Monitor Agent** or **Log Analytics Agent** must be installed on target machines
- **VM Insights** solution must be enabled in the workspace
- **Dependency Agent** must be deployed (for enhanced data collection)

#### Data Collected:
- Computer name, hostname, and DNS names
- Operating system details (name, version, family)
- Physical memory capacity
- Boot time information
- Azure-specific metadata (subscription, resource group, location)
- Network interface information
- Agent health status

#### Configuration Steps:
1. Navigate to your Log Analytics workspace in Azure Portal
2. Go to **Virtual machines** under **Workspace Data Sources**
3. Connect target VMs to the workspace
4. Enable **VM Insights** from the Insights section
5. Deploy the Dependency Agent alongside the monitoring agent

#### Validation Query:
```kusto
VMComputer
| where TimeGenerated > ago(24h)
| summarize ComputerCount = dcount(Computer)
```

---

### 2. VMProcess Table (Essential)
The VMProcess table provides detailed process information critical for application discovery and monitoring.

#### Prerequisites:
- **VM Insights** must be enabled with process and dependency collection
- **Dependency Agent** must be installed and running
- Process and dependency collection must be explicitly enabled (disabled by default to save costs)

#### Data Collected:
- Process names and executable paths
- Command line arguments
- Process IDs and parent processes
- User context
- Start times
- Product and version information
- Resource consumption metrics

#### Configuration Steps:
1. In your Log Analytics workspace, navigate to **Insights** > **Virtual Machines**
2. Click **Configure Insights**
3. Enable **Collect guest performance counters and dependencies**
4. Select **Enable processes and dependencies collection**
5. Deploy Dependency Agent to all target machines
6. Allow 15-30 minutes for data to begin flowing

#### Important Notes:
- Process collection increases data ingestion costs
- By default, process data is NOT collected to minimize costs
- Required for application discovery and dependency mapping features

#### Validation Query:
```kusto
VMProcess
| where TimeGenerated > ago(1h)
| summarize ProcessCount = dcount(Process) by Computer
| order by ProcessCount desc
```

---

### 3. VMConnection Table (Essential)
The VMConnection table tracks network connections and is vital for understanding application communications and dependencies.

#### Prerequisites:
- **VM Insights** with dependency collection enabled
- **Dependency Agent** installed and configured
- Network monitoring permissions configured

#### Data Collected:
- Source and destination IPs
- Port information
- Connection state and direction
- Bytes sent/received
- Response times
- Process associations
- Connection failure information
- Protocol details (TCP/UDP)

#### Configuration Steps:
1. Ensure VM Insights is enabled with dependency collection
2. Verify Dependency Agent is installed on all machines
3. Check firewall rules allow monitoring of network connections
4. For Linux systems, ensure the agent has appropriate permissions

#### Network Monitoring Considerations:
- Physical network connections are aggregated into logical connections
- Data is grouped into 1-minute intervals
- Malicious IP detection is automatically performed
- Both inbound and outbound connections are tracked

#### Validation Query:
```kusto
VMConnection
| where TimeGenerated > ago(1h)
| summarize ConnectionCount = count() by Computer, Direction
| order by ConnectionCount desc
```

---

## Optional Performance Monitoring Configuration

### Process-Level CPU Monitoring (Perf Table)
By default, the Perf table does not collect process-level CPU data. This configuration enables detailed CPU usage tracking per process.

#### Why Configure This:
- Track CPU usage by individual processes
- Identify resource-intensive applications
- Perform capacity planning and optimization
- Troubleshoot performance issues

#### Configuration Steps:

1. **Navigate to Legacy Agent Configuration**
   - Open your Log Analytics workspace
   - Go to **Legacy agents management** (under Settings)
   - Select **Windows performance counters** or **Linux performance counters**

2. **Add Process Performance Counters**
   
   For Windows systems, add these counters:
   - Object: `Process`
   - Counter: `% Processor Time`
   - Instance: `*` (all processes)
   - Interval: `60` seconds (adjust based on needs)
   
   Additional recommended counters:
   - `Process(*)% User Time`
   - `Process(*)Private Bytes`
   - `Process(*)Working Set`
   - `Process(*)Handle Count`

3. **Configure Collection Interval**
   - Default: 60 seconds
   - High-frequency monitoring: 10-30 seconds (increases cost)
   - Low-frequency monitoring: 120-300 seconds (reduces cost)

4. **Apply Configuration**
   - Click **Add** for each counter
   - Changes take effect within 5-15 minutes
   - Verify data collection using validation queries

#### Validation Query for Process CPU:
```kusto
Perf
| where TimeGenerated > ago(1h)
| where ObjectName == "Process" 
| where CounterName == "% Processor Time"
| where InstanceName != "_Total" and InstanceName != "Idle"
| summarize AvgCPU = avg(CounterValue) by Computer, InstanceName
| where AvgCPU > 5
| order by AvgCPU desc
```

#### Cost Considerations:
- Process-level performance monitoring significantly increases data ingestion
- Estimate: ~2-5 GB per server per month for process CPU monitoring
- Consider using sampling or filtering for cost optimization

---

## Additional Recommended Tables

### VMBoundPort Table
Tracks open ports and listening services.

**Enable by**: Installing Dependency Agent with VM Insights

**Use cases**: Security auditing, service discovery, port inventory

### InsightsMetrics Table
Contains aggregated performance metrics.

**Enable by**: Enabling VM Insights

**Use cases**: Overall CPU/memory/disk utilization, trend analysis

### Heartbeat Table
Monitors agent connectivity and health.

**Enable by**: Automatically collected when agents are installed

**Use cases**: Agent health monitoring, connectivity tracking

---

## Verification Checklist

After configuration, verify the following:

- [ ] VMComputer table receiving data (run validation query)
- [ ] VMProcess table showing processes (check record count)
- [ ] VMConnection table capturing network data (verify connections)
- [ ] Dependency Agent status is "Healthy" on all VMs
- [ ] VM Insights showing topology maps
- [ ] (Optional) Perf table collecting process CPU if configured
- [ ] Data ingestion costs are within budget

---

## Troubleshooting Common Issues

### No Data in VMProcess/VMConnection Tables
- Verify Dependency Agent is installed and running
- Check that process and dependency collection is enabled in VM Insights
- Wait 30 minutes after configuration changes
- Review agent logs for errors

### Missing Computers in VMComputer
- Confirm Log Analytics agent is installed and connected
- Check workspace ID and key configuration
- Verify network connectivity to Azure endpoints
- Review workspace data retention settings

### High Data Ingestion Costs
- Review process collection frequency
- Consider filtering unnecessary processes
- Adjust performance counter collection intervals
- Implement data sampling strategies

---

## Support and Resources

- [Azure Monitor VM Insights Documentation](https://docs.microsoft.com/azure/azure-monitor/vm/vminsights-overview)
- [Log Analytics Agent Troubleshooting](https://docs.microsoft.com/azure/azure-monitor/agents/agent-troubleshoot)
- [Dependency Agent Installation Guide](https://docs.microsoft.com/azure/azure-monitor/vm/vminsights-dependency-agent)
- [KQL Query Reference](https://docs.microsoft.com/azure/data-explorer/kusto/query/)

---

## Contact Information

For additional assistance with Log Analytics configuration for OmniGaze:
- Consult your Azure administrator
- Review OmniGaze integration documentation
- Contact OmniGaze support team

---

*Document Version: 1.0*  
*Last Updated: 2025-01-09*  
*Applies to: OmniGaze 5.0 and later*