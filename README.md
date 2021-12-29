# UniversalTunTapDriver
------
## A driver for TUN/TAP devices to support basic operations on both linux and windows platform.

UniversalTunTapDriver is a lightweight library which allows you to  control TUN/TAP devices on your **windows** or **linux** machine easily.

 

----------
### **UniversalTunTapDriver release list**
#### ***UniversalTunTapDriver V1.1***
released in *Aug 21, 2021*
> * Add TunIOManager to organize the I/O operation of a TUN device
> * Fix some bugs
> * Support asynchronous I/O on linux platform

#### ***UniversalTunTapDriver V1.0***
released in *Jan 19, 2021*
> * Update form **TunTapDriver-windows*** project
> * Add support for **linux** platform
> * Fix some bugs

#### ***TunTapDriver-windows V1.0***
released in *Sep 30, 2020*
> * Upload document and test project
> * Fix some bugs

#### ***TunTapDriver-windows V0.9.9***
released in *Aug 22, 2020*
> * Upload code
> * Open source under **MPL2.0 License**

*This project is **TunTapDriver-windows** before Jan 19, 2021. TunTapDriver-windows only support to control TUN/TAP device under windows platform. All the features in the previous are included in **UniversalTunTapDriver**  project.

----------


### **TODO LIST**

- [x] Fix some bugs when running on linux platform
- [ ] Finish the **UNFINISHED** code
- [ ] Develop and test the control abality of TAP devices on windows and linux platform.
- [x] Open source under MPL2.0 License
- [x] Support to control TUN devices on linux platform
- [x] Support to control TUN devices on windows platform


----------


### **How to use**

#### **1.Clone the repository**

```bash
git clone https://github.com/HBSnail/UniversalTunTapDriver.git
```

#### **2.Compile the source code**

```
This process should be done by yourself.
```

#### **3.Add reference to your own project**

```
This process should be done by yourself.
```

#### **4.Use the APIs we offers in your application**

##### **4.0 Get all of the TUN/TAP devices installed on your computer**
```csharp
 // The following code only works on windows
 // On linux please use "ifconfig" in the terminal for enumerating all network interfaces
 //On windows you MUST install 'TAP-Windows Adapter V9' before execute the code
 List<TunTapDeviceInfo> DeviceList  = GetTapGuidList("tap0901");
 
 //TunTapDeviceInfo is a kind of structure defined as follow
 /*
     public struct TunTapDeviceInfo
        {
            public string Name;
            public string Guid;
            public TunTapDeviceInfo(string n, string g)
            {
                Name = n;
                Guid = g;
            }
        }
 */
```
##### **4.1 Create&initial the deivce**
```csharp
 // On linux please set the name and guid to the same value in the structure TunTapDeviceInfo. like "tun0" "tap0" ect.
    TunTapDeviceInfo dInfo; 
    dInfo.Name = "NAME";
    dInfo.Guid = "GUID";
    TunTapDevice Device = New TunTapDevice(dInfo);
 // After this you will successfully create and initial a TUN/TAP device except the name or guid does not exist or the divice was occupied by other process. 
```
##### **4.2 Config&set device states**
```csharp
 // The following code only works on windows
 // On linux please use "ifconfig" or "ip" in the terminal.

 Device.ConfigTun(IPAddress.Parse("LOC_IP"), IPAddress.Parse("REM_IP"), IPAddress.Parse("NET_MASK"));
 Device.SetConnectionState(ConnectionStatus.Connected);

```
##### **4.3 Create&get device I/O stream**
```csharp
 Device.CreateDeviceIOStream(1500);
 FileStream DeviceIOStream = Device.TunTapDeviceIOStream;
```

##### **4.4 READ&WRITE the I/O stream to read&write TUN/TAP devices.**
``` 
This process should be done by yourself.
```

----------

### **Reference project**
Thanks!

 - [openvpn][2]
 - [tap-windows6][3]
 - [toyvpn][4]
 - [tun-go][5]


----------


Auther: [HBSnail][1]     
Aug 21, 2021

[1]: https://github.com/HBSnail
[2]: https://github.com/OpenVPN/openvpn
[3]: https://github.com/OpenVPN/tap-windows6
[4]: https://android.googlesource.com/platform/development/+/master/samples/ToyVpn
[5]: https://github.com/Alienero/tun-go
