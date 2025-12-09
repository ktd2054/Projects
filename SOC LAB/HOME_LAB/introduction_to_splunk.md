# Splunk

- leading SIEM solutions

## Splunk Components

- Splunk Forwarder

  Collects data and send it to splunk instance
  
  Web server generating web traffic.
  
  Windows machine generating Windows Event Logs, PowerShell, and Sysmon data.
  
  Linux host generating host-centric logs.
  
  Database generating DB connection requests, responses, and errors.
  
- Splunk Indexer

  Receives data from forwarder and process the data.

  Parses and normalizes data into field-value pairs, categorizes it and stores the results as event

    
- Search Head

To search indexed logs using SPL (Search Processing Language).


***************************************************************************

Splunk can ingest any data and after data is added to splunk, it is processes and transformed into series of individual events.

The data Sources can be event logs, website logs, firewall logs etc.



