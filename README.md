# SoftEther Autoinstaller

This is my SoftEther autoinstaller. This will compile and install SoftEther onto your server. This installer in particular will set up SoftEther as a system service. Currently Ubuntu and CentOS are supported.

## Ubuntu 16.04+
### 64-bit
```bash
wget -O install https://raw.githubusercontent.com/icoexist/softether-autoinstall/master/ubuntu/x64/se-install-ubuntu.bash && chmod 770 install && ./install
```

### 32-bit
```bash
wget -O install https://raw.githubusercontent.com/icoexist/softether-autoinstall/master/ubuntu/x86/se-install-ubuntu-x86.bash && chmod 770 install && ./install
```
Please bear in mind that running 32-bit versions of Ubuntu server is not recommended, and Ubuntu 18.04 is **not** available in a 32-bit version.

## Ubuntu 14.04
### 64-bit
```bash
wget -O install https://raw.githubusercontent.com/icoexist/softether-autoinstall/master/ubuntu-14.04/x64/se-install-ubuntu.bash && chmod 770 install && ./install
```

## CentOS
### 64-bit
```bash
curl -o install https://raw.githubusercontent.com/icoexist/softether-autoinstall/master/centos/x64/se-install-centos.bash && chmod 770 install && ./install
```

### 32-bit
[WIP]

## Configure SoftEther
### Execute vpncmd
To execute SoftEther's cmd utility, use `sudo /usr/local/vpnserver/vpncmd` <-- This applies if you used my scripts. If you've installed SE yourself, find the vpnserver directory.

With `vpncmd` you are able to change every option in regard to SoftEther. It has the same exact purpose for the GUI version you can obtain on MacOS and Windows. I encourage people to use `vpncmd` because it can be easier than the GUI, plus there's no need to download anything since you can configure the entire server from an SSH session.

### Set a server password
It is important that you set a server password. This should be the first thing you do after launching the `vpncmd` utility. To set a password, type `serverpasswordset` into your terminal after you've launched the `vpncmd` utility. For verification, you have to type the password twice.

### Quick-start Guide
This section will provide you with a list of things to get you started with your VPN server. I'll have more commands listed below this section.

1. Start the `vpncmd` utility with `sudo /usr/local/vpncmd`
2. Set a server password with `serverpasswordset`
3. Select the DEFAULT hub with `hub default`
4. Create a new user with `usercreate` | You can either use `usercreate` or `usercreate [uesrname]`
5. Set a password for the new user with `userpasswordset` | You can either use `userpasswordset` or `userpasswordset [uesrname]`
6. Enable SecureNAT for the DEFAULT hub with `securenatenable`

   Optional: You can enable L2TP/IPsec with `ipsecenable`. It is recommended that if you use this option, you only enable L2TP/IPsec. Do not enable RAW L2TP w/o encrpytion. You will be asked to set a pre-shared key for the IPsec server, you can use anything. I've used `vpn` as a pre-shared key for ages. Remember that this is NOT a password for the server or a user, so it's safe to use that. You'll also be asked for the default hub in the event that a user does not specify the hub to connect to in their username, you'll set this to `default` if you haven't changed any hub names. If you're more advanced user and have multiple hubs, you can specify what hub a user connects to by putting it in their username on the client. For instance `icoexist@public` or `icoexist@hub2`.
   
If everything was done properly, you're ready to use your new VPN server! To add new users, just launch the `vpncmd` utility and repeat steps 3 - 5.

### Commands List 

 `About`                      - Display the version information   
 `AcAdd`                      - Add Rule to Source IP Address Limit List (IPv4)   
 `AcAdd6`                     - Add Rule to Source IP Address Limit List (IPv6)   
 `AcDel`                      - Delete Rule from Source IP Address Limit List   
 `AcList`                     - Get List of Rule Items of Source IP Address Limit List   
 `AccessAdd`                  - Add Access List Rules (IPv4)   
 `AccessAdd6`                 - Add Access List Rules (IPv6)   
 `AccessAddEx`                - Add Extended Access List Rules (IPv4: Delay, Jitter and Packet Loss Generating)   
 `AccessAddEx6`               - Add Extended Access List Rules (IPv6: Delay, Jitter and Packet Loss Generating)   
 `AccessDelete`               - Delete Rule from Access List   
 `AccessDisable`              - Disable Access List Rule   
 `AccessEnable`               - Enable Access List Rule   
 `AccessList`                 - Get Access List Rule List    
 `AdminOptionList`            - Get List of Virtual Hub Administration Options   
 `AdminOptionSet`             - Set Values of Virtual Hub Administration Options   
 `BridgeCreate`               - Create Local Bridge Connection   
 `BridgeDelete`               - Delete Local Bridge Connection   
 `BridgeDeviceList`           - Get List of Network Adapters Usable as Local Bridge   
 `BridgeList`                 - Get List of Local Bridge Connection   
 `CAAdd`                      - Add Trusted CA Certificate   
 `CADelete`                   - Delete Trusted CA Certificate   
 `CAGet`                      - Get Trusted CA Certificate   
 `CAList`                     - Get List of Trusted CA Certificates   
 `Caps`                       - Get List of Server Functions/Capability   
 `CascadeAnonymousSet`        - Set User Authentication Type of Cascade Connection to Anonymous Authentication   
 `CascadeCertGet`             - Get Client Certificate to Use for Cascade Connection   
 `CascadeCertSet`             - Set User Authentication Type of Cascade Connection to Client Certificate Authentication   
 `CascadeCompressDisable`     - Disable Data Compression when Communicating by Cascade Connection   
 `CascadeCompressEnable`      - Enable Data Compression when Communicating by Cascade Connection   
 `CascadeCreate`              - Create New Cascade Connection   
 `CascadeDelete`              - Delete Cascade Connection Setting   
 `CascadeDetailSet`           - Set Advanced Settings for Cascade Connection   
 `CascadeEncryptDisable`      - Disable Encryption when Communicating by Cascade Connection   
 `CascadeEncryptEnable`       - Enable Encryption when Communicating by Cascade Connection   
 `CascadeGet`                 - Get the Cascade Connection Setting   
 `CascadeList`                - Get List of Cascade Connections   
 `CascadeOffline`             - Switch Cascade Connection to Offline Status   
 `CascadeOnline`              - Switch Cascade Connection to Online Status   
 `CascadePasswordSet`         - Set User Authentication Type of Cascade Connection to Password Authentication   
 `CascadePolicySet`           - Set Cascade Connection Session Security Policy   
 `CascadeProxyHttp`           - Set Connection Method of Cascade Connection to be via an HTTP Proxy Server   
 `CascadeProxyNone`           - Specify Direct TCP/IP Connection as the Connection Method of Cascade Connection   
 `CascadeProxySocks`          - Set Connection Method of Cascade Connection to be via an SOCKS Proxy Server   
 `CascadeRename`              - Change Name of Cascade Connection   
 `CascadeServerCertDelete`    - Delete the Server Individual Certificate for Cascade Connection   
 `CascadeServerCertDisable`   - Disable Cascade Connection Server Certificate Verification Option   
 `CascadeServerCertEnable`    - Enable Cascade Connection Server Certificate Verification Option   
 `CascadeServerCertGet`       - Get the Server Individual Certificate for Cascade Connection   
 `CascadeServerCertSet`       - Set the Server Individual Certificate for Cascade Connection   
 `CascadeSet`                 - Set the Destination for Cascade Connection   
 `CascadeStatusGet`           - Get Current Cascade Connection Status   
 `CascadeUsernameSet`         - Set User Name to Use Connection of Cascade Connection   
 `Check`                      - Check whether SoftEther VPN Operation is Possible   
 `ClusterConnectionStatusGet` - Get Connection Status to Cluster Controller   
 `ClusterMemberCertGet`       - Get Cluster Member Certificate   
 `ClusterMemberInfoGet`       - Get Cluster Member Information   
 `ClusterMemberList`          - Get List of Cluster Members   
 `ClusterSettingController`   - Set VPN Server Type as Cluster Controller   
 `ClusterSettingGet`          - Get Clustering Configuration of Current VPN Server   
 `ClusterSettingMember`       - Set VPN Server Type as Cluster Member   
 `ClusterSettingStandalone`   - Set VPN Server Type as Standalone   
 `ConfigGet`                  - Get the current configuration of the VPN Server   
 `ConfigSet`                  - Write Configuration File to VPN Server   
 `ConnectionDisconnect`       - Disconnect TCP Connections Connecting to the VPN Server   
 `ConnectionGet`              - Get Information of TCP Connections Connecting to the VPN Server   
 `ConnectionList`             - Get List of TCP Connections Connecting to the VPN Server   
 `Crash`                      - Raise a error on the VPN Server / Bridge to terminate the process forcefully.   
 `CrlAdd`                     - Add a Revoked Certificate   
 `CrlDel`                     - Delete a Revoked Certificate   
 `CrlGet`                     - Get a Revoked Certificate   
 `CrlList`                    - Get List of Certificates Revocation List   
 `Debug`                      - Execute a Debug Command   
 `DhcpDisable`                - Disable Virtual DHCP Server Function of SecureNAT Function   
 `DhcpEnable`                 - Enable Virtual DHCP Server Function of SecureNAT Function   
 `DhcpGet`                    - Get Virtual DHCP Server Function Setting of SecureNAT Function   
 `DhcpSet`                    - Change Virtual DHCP Server Function Setting of SecureNAT Function   
 `DhcpTable`                  - Get Virtual DHCP Server Function Lease Table of SecureNAT Function   
 `DynamicDnsGetStatus`        - Show the Current Status of Dynamic DNS Function   
 `DynamicDnsSetHostname`      - Set the Dynamic DNS Hostname   
 `EtherIpClientAdd`           - Add New EtherIP / L2TPv3 over IPsec Client Setting to Accept EthreIP / L2TPv3 Client Devices   
 `EtherIpClientDelete`        - Delete an EtherIP / L2TPv3 over IPsec Client Setting   
 `EtherIpClientList`          - Get the Current List of EtherIP / L2TPv3 Client Device Entry Definitions   
 `ExtOptionList`              - Get List of Virtual Hub Extended Options   
 `ExtOptionSet`               - Set a Value of Virtual Hub Extended Options   
 `Flush`                      - Save All Volatile Data of VPN Server / Bridge to the Configuration File   
 `GroupCreate`                - Create Group   
 `GroupDelete`                - Delete Group   
 `GroupGet`                   - Get Group Information and List of Assigned Users   
 `GroupJoin`                  - Add User to Group   
 `GroupList`                  - Get List of Groups   
 `GroupPolicyRemove`          - Delete Group Security Policy   
 `GroupPolicySet`             - Set Group Security Policy   
 `GroupSet`                   - Set Group Information   
 `GroupUnjoin`                - Delete User from Group   
 `Hub`                        - Select Virtual Hub to Manage   
 `HubCreate`                  - Create New Virtual Hub   
 `HubCreateDynamic`           - Create New Dynamic Virtual Hub (For Clustering)   
 `HubCreateStatic`            - Create New Static Virtual Hub (For Clustering)   
 `HubDelete`                  - Delete Virtual Hub   
 `HubList`                    - Get List of Virtual Hubs   
 `HubSetDynamic`              - Change Virtual Hub Type to Dynamic Virtual Hub   
 `HubSetStatic`               - Change Virtual Hub Type to Static Virtual Hub   
 `IPsecEnable`                - Enable or Disable IPsec VPN Server Function   
 `IPsecGet`                   - Get the Current IPsec VPN Server Settings   
 `IpDelete`                   - Delete IP Address Table Entry   
 `IpTable`                    - Get the IP Address Table Database   
 `KeepDisable`                - Disable the Keep Alive Internet Connection Function   
 `KeepEnable`                 - Enable the Keep Alive Internet Connection Function   
 `KeepGet`                    - Get the Keep Alive Internet Connection Function   
 `KeepSet`                    - Set the Keep Alive Internet Connection Function   
 `LicenseAdd`                 - Add License Key Registration   
 `LicenseDel`                 - Delete Registered License   
 `LicenseList`                - Get List of Registered Licenses   
 `LicenseStatus`              - Get License Status of Current VPN Server   
 `ListenerCreate`             - Create New TCP Listener   
 `ListenerDelete`             - Delete TCP Listener   
 `ListenerDisable`            - Stop TCP Listener Operation   
 `ListenerEnable`             - Begin TCP Listener Operation   
 `ListenerList`               - Get List of TCP Listeners   
 `LogDisable`                 - Disable Security Log or Packet Log   
 `LogEnable`                  - Enable Security Log or Packet Log   
 `LogFileGet`                 - Download Log file   
 `LogFileList`                - Get List of Log Files   
 `LogGet`                     - Get Log Save Setting of Virtual Hub   
 `LogPacketSaveType`          - Set Save Contents and Type of Packet to Save to Packet Log   
 `LogSwitchSet`               - Set Log File Switch Cycle   
 `MacDelete`                  - Delete MAC Address Table Entry   
 `MacTable`                   - Get the MAC Address Table Database   
 `MakeCert`                   - Create New X.509 Certificate and Private Key (1024 bit)   
 `MakeCert2048`               - Create New X.509 Certificate and Private Key (2048 bit)   
 `NatDisable`                 - Disable Virtual NAT Function of SecureNAT Function   
 `NatEnable`                  - Enable Virtual NAT Function of SecureNAT Function   
 `NatGet`                     - Get Virtual NAT Function Setting of SecureNAT Function   
 `NatSet`                     - Change Virtual NAT Function Setting of SecureNAT Function   
 `NatTable`                   - Get Virtual NAT Function Session Table of SecureNAT Function   
 `Offline`                    - Switch Virtual Hub to Offline   
 `Online`                     - Switch Virtual Hub to Online   
 `OpenVpnEnable`              - Enable / Disable OpenVPN Clone Server Function   
 `OpenVpnGet`                 - Get the Current Settings of OpenVPN Clone Server Function   
 `OpenVpnMakeConfig`          - Generate a Sample Setting File for OpenVPN Client   
 `OptionsGet`                 - Get Options Setting of Virtual Hubs   
 `PolicyList`                 - Display List of Security Policy Types and Settable Values   
 `RadiusServerDelete`         - Delete Setting to Use RADIUS Server for User Authentication   
 `RadiusServerGet`            - Get Setting of RADIUS Server Used for User Authentication   
 `RadiusServerSet`            - Set RADIUS Server to use for User Authentication   
 `Reboot`                     - Reboot VPN Server Service   
 `RouterAdd`                  - Define New Virtual Layer 3 Switch   
 `RouterDelete`               - Delete Virtual Layer 3 Switch   
 `RouterIfAdd`                - Add Virtual Interface to Virtual Layer 3 Switch   
 `RouterIfDel`                - Delete Virtual Interface of Virtual Layer 3 Switch   
 `RouterIfList`               - Get List of Interfaces Registered on the Virtual Layer 3 Switch   
 `RouterList`                 - Get List of Virtual Layer 3 Switches   
 `RouterStart`                - Start Virtual Layer 3 Switch Operation   
 `RouterStop`                 - Stop Virtual Layer 3 Switch Operation   
 `RouterTableAdd`             - Add Routing Table Entry for Virtual Layer 3 Switch   
 `RouterTableDel`             - Delete Routing Table Entry of Virtual Layer 3 Switch   
 `RouterTableList`            - Get List of Routing Tables of Virtual Layer 3 Switch    
 `SecureNatDisable`           - Disable the Virtual NAT and DHCP Server Function (SecureNat Function)   
 `SecureNatEnable`            - Enable the Virtual NAT and DHCP Server Function (SecureNat Function)   
 `SecureNatHostGet`           - Get Network Interface Setting of Virtual Host of SecureNAT Function   
 `SecureNatHostSet`           - Change Network Interface Setting of Virtual Host of SecureNAT Function   
 `SecureNatStatusGet`         - Get the Operating Status of the Virtual NAT and DHCP Server Function (SecureNat Function)   
 `ServerCertGet`              - Get SSL Certificate of VPN Server   
 `ServerCertRegenerate`       - Generate New Self-Signed Certificate with Specified CN (Common Name) and Register on VPN Server   
 `ServerCertSet`              - Set SSL Certificate and Private Key of VPN Server   
 `ServerCipherGet`            - Get the Encrypted Algorithm Used for VPN Communication.   
 `ServerCipherSet`            - Set the Encrypted Algorithm Used for VPN Communication.   
 `ServerInfoGet`              - Get server information   
 `ServerKeyGet`               - Get SSL Certificate Private Key of VPN Server   
 `ServerPasswordSet`          - Set VPN Server Administrator Password   
 `ServerStatusGet`            - Get Current Server Status   
 `SessionDisconnect`          - Disconnect Session   
 `SessionGet`                 - Get Session Information   
 `SessionList`                - Get List of Connected Sessions   
 `SetEnumAllow`               - Allow Enumeration by Virtual Hub Anonymous Users   
 `SetEnumDeny`                - Deny Enumeration by Virtual Hub Anonymous Users   
 `SetHubPassword`             - Set Virtual Hub Administrator Password   
 `SetMaxSession`              - Set the Max Number of Concurrently Connected Sessions for Virtual Hub   
 `SstpEnable`                 - Enable / Disable Microsoft SSTP VPN Clone Server Function   
 `SstpGet`                    - Get the Current Settings of Microsoft SSTP VPN Clone Server Function   
 `StatusGet`                  - Get Current Status of Virtual Hub   
 `SyslogDisable`              - Disable syslog Send Function   
 `SyslogEnable`               - Set syslog Send Function   
 `SyslogGet`                  - Get syslog Send Function   
 `TrafficClient`              - Run Network Traffic Speed Test Tool in Client Mode   
 `TrafficServer`              - Run Network Traffic Speed Test Tool in Server Mode   
 `UserAnonymousSet`           - Set Anonymous Authentication for User Auth Type   
 `UserCertGet`                - Get Certificate Registered for Individual Certificate Authentication User   
 `UserCertSet`                - Set Individual Certificate Authentication for User Auth Type and Set Certificate   
 `UserCreate`                 - Create User    
 `UserDelete`                 - Delete User   
 `UserExpiresSet`             - Set User's Expiration Date   
 `UserGet`                    - Get User Information   
 `UserList`                   - Get List of Users   
 `UserNTLMSet`                - Set NT Domain Authentication for User Auth Type   
 `UserPasswordSet`            - Set Password Authentication for User Auth Type and Set Password   
 `UserPolicyRemove`           - Delete User Security Policy   
 `UserPolicySet`              - Set User Security Policy   
 `UserRadiusSet`              - Set RADIUS Authentication for User Auth Type   
 `UserSet`                    - Change User Information   
 `UserSignedSet`              - Set Signed Certificate Authentication for User Auth Type   
 `VpnAzureGetStatus`          - Show the current status of VPN Azure function   
 `VpnAzureSetEnable`          - Enable / Disable VPN Azure Function   
 `VpnOverIcmpDnsEnable`       - Enable / Disable the VPN over ICMP / VPN over DNS Server Function   
 `VpnOverIcmpDnsGet`          - Get Current Setting of the VPN over ICMP / VPN over DNS Function   