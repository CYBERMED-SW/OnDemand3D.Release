# OnDemand3DApp 1.0.11.1007.110626

**Version:** 1.0.11.1007.110626  
**Release date:** 2026-11  
**Publisher:** Cybermed Co., Ltd.

This release changes the database access layer, fixes issues in X-Report, LeafImplant and 3D Ceph, and ships the required runtime components with the installer and the portable viewer.

---

## What's new

### Database: OLE DB replaced by ODBC
- OnDemand3DApp and OnDemand3D Server now access the database through **ODBC** instead of OLE DB.
- **Fixed:** the application could hang (deadlock) when the latest Microsoft Office (Microsoft 365) was installed or running on the same PC.
- Local databases use the *Microsoft Access ODBC driver*; server databases use *ODBC Driver 17 for SQL Server*.
- Existing databases are used as they are. No migration step is needed.

### Prerequisites included in the installer
The installer now includes the components the application needs:

| Component | Purpose |
|---|---|
| Microsoft Edge WebView2 Runtime (x64) | Embedded web views |
| Microsoft Visual C++ Redistributable (x64) | Runtime libraries |
| Microsoft Access Database Engine (x64) | Local database (Access ODBC driver) |
| ODBC Driver 17 for SQL Server (x64) | Server database |
| Sentinel HASP driver | License key |

### Portable viewer (OnDemand3D Communicator) on export
- **New option:** *Include Prerequisites* in **DBM > CD/DVD/USB Writer > Recording Options**.
  - **On:** the exported media contains the runtime components the viewer needs (WebView2, Visual C++ Redistributable, Access Database Engine). The media is larger (about +250 MB).
  - **Off:** only the viewer and the images are exported.
- When the viewer starts from the media (`launcher.exe`), it checks the required components and installs any that are missing.

---

## Bug fixes

| Area | Fix |
|---|---|
| X-Report | Pages captured with the **Capture** button were not saved. They are now saved and can be reopened. |
|  | Scrolling did not work correctly on **Windows 11 24H2 and later**. (tested 24H2,25H2, 26H2)|
|  | Tested environments: Windows 11 (24H2 and 25H2 and 26H2) |
| LeafImplant | The program closed unexpectedly after login. |
| 3D Ceph | Automatic landmark detection crashed or returned no values for CT data with a different Pixel Representation |
|  | The landmark library was updated with the version, and its 3rd party components are now included in the distribution. |

---


## System requirements

- Windows 10 / Windows 11 (64-bit)
- Required runtime components are installed by the installer (see above).
- A valid license key

## Upgrade notes

- Existing local and server databases are used as they are; no conversion is needed.
- OnDemand3DApp can now be used while Microsoft Office (including Microsoft 365) is open.
