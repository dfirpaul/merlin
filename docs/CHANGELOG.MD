# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## 0.6.0 - 2018-07-29
### Added
- Added support for QUIC protocol version Q39 to both Server and Agent
- Added `-proto` command line flag for both Server and Agent
- Added Server struct with New and Run methods to http2 lib
- Added `github.com/lucas-clemente/quic-go` & supporting libs to Vendor
- Added check for publicly distributed Merlin x.509 testing certificate
- Added Job struct, GetMessageForJob function, and AddJob function to agents.go
- Added GetAgentStatus function to agents.go
- Added proto and status to table output for agent or session information
- Added RemoveAgent fuction to agents.go
- Added remove command to main menu to remove DEAD agents
- Added info command to module menu as a shortcut for show info
- Added data/html to server distrobution files
- Added agent-javascript to Make file to update version and build info

### Changed
- Server CLI starts first, then web server
- Renamed http2 `handler` function to `agentHandler`
- Agent struct to have `Client` and `UserAgen` fields
- Default User-Agent for client connections to `Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.85 Safari/537.36`
- Renamed agent `getH2WebClient` function to `getClient`
- channel type to Job for agent struct in agents.go
- agents.StatusCheckIn to return error type
- QUIC idle timeout to 1 week
- agent struct to export initial and status check in values
- agent struct to have communication protocol value
- AgentInfo struct to have proto and embeded SysInfo struct
- Updated tablewriter library to latest version
- Updated merlin.js agent to use new embeded SysInfo struct
- Updated Make file to output files in folder of the build number
- Updated MerlinAgentDLL main.go functions to use correct params
- Merlin Server listens on 127.0.0.1 by default

### Removed
- Removed AddChannel function from agents.go

## 0.5.4 - 2018-07-17
### Added
- Added Get-ScheduledTaskComHandler module
- Added Invoke-PowerThIEf module

## 0.5.3 - 2018-07-04
### Fixed
- Fixed #21 by changing `strings.TrimRight()` to `strings.TrimSuffix()`

## 0.5.2 - 2018-06-13
### Added
- Added 4 modules from @HarmJ0y's Discretionary ACL Modification Project (DAMP)
- Added Add-RemoteRegBackdoor module
- Added Get-RemoteCachedCredential module
- Added Get-RemoteLocalAccountHash module
- Added Get-RemoteMachineAccountHash module

## 0.5.1 - 2018-05-26
### Added
- Added DSCompromised-Configure-Victim module
- Added Create-HotKeyLN module
- Added Get-OSTokenInformation module
- Added Invoke-WMILM module

## 0.5.0 - 2018-05-26
Version numbers changed drastically to start following semantic versioning
### Added
- Module reload command to instantiate a new, clean object
- windows/x64/powershell/privesc/psgetsystem.json module
- linux/x64/bash/credentials/MimiPenguin.json module (@ahhh)
- linux/x64/bash/troll/Prank.json module (@ahhh)
- windows/x64/powershell/persistence/Invoke-ADSBackdoor.json module (@ahhh)
- Merlin agent DLL
- Invoke-Merlin PowerShell script
- Package compiled agents with releases in data/bin directory

### Changed
- Updated existing linux modules to use the /bin/sh shell
- Updated module template file base.json to include _credits_
- Make file to support compiling DLL
- cmd/merlinagent/main.go into several packages and struct in
pkg/agent/main.go
- Renamed pkg/agent/agent.go to pkg/agent/exec.go
- Version numbers to follow semantic versioning
- Added "agent" to the table for a module's options (@0xada4d)
- Added _credits_ to modules.go
- Updated main README.MD

### Fixed
- Null use command caused shell to exit
- Module set option verbose output to new value instead of original
- Agent upload error message invalid memory address or nil pointer dereference

## 0.1.4 - 2018-03-02
### Added
- Time skew to sleep by @ahhh
- IP address information from agents by @ahhh
- MIPS and ARM agent compile instructions to Make file by @twigatech
- File upload from server to agent by @twigatech
- .gitignore for data directory by @twigatech
- Merlin JavaScript Agent
- Merlin JavaScript Agent test page in `data/html`
- CORS header "Access-Control-Allow-Origin: *" to every response
- Server handling for OPTIONS request to facilitate JavaScript XHR requests
- Thanks to JetBrains for an open source license
- This CHANGELOG
- Module support
- Multiple Windows and Linux modules
- Module README on how to create a module
- Execute commands on the host operating system from Merlin prompt
- Execute module on "all" agents

### Changed
- Menu system from one long command to multiple menus
- Merlin Server from 1 large file to multiple library files in `pkg`
- Make file instructions for Merlin version number
- Agent command execution to send back argument processing errors


## 0.1.3 - 2017-12-17
### Added
- First public release

## 0.1.2 - 2017-01-13
### Added
- Makefile to make building the server and agent easier
- New libraries to help with displaying information in formatted tables
- Tab completion for commands issued on the server

### Changed
- Agent to include a random padding of up to 4096 bytes per message to
 help prevent detection based off consistent message size.


## 0.1.0 - 2017-06-10

This release marks a stable BETA version of Merlin. Both the server and
the agent cross-compile to Windows, Linux, and MacOS. The 64 bit version
 of the agent binaries for all 3 platform can be found in data\bin. The
32 bit binaries are not provided, but could be compiled if you desire.
Check the README in the data\bin directory. To run this release,
download Merlin_v0.1Beta.zip and unzip the contents. Next, download the
applicable binary for your platform (i.e. merlinserver_windows_x64.exe)
and place it in the root of that unzipped folder. The binary can be run
from the command line. Alternatively, Merlin can be run directly as a go
 script with go run cmd\merlinserver.go.