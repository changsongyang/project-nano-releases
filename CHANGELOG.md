# Change Log

## [1.4.0] - 2024-05-05

### 新增

- Core: 配置文件"domain.cfg"增加选项timeout，设置超时时间，单位为秒，默认值10
- Cell: 配置文件"data/instance.data"新增选项max_guest设置当前节点允许承载的最大云主机数量，默认值100
- Cell: 配置文件"domain.cfg"新增选项timeout，设置操作超时时间，单位为秒，默认值10
- FrontEnd: 配置文件"frontend.cfg"新增选项max_cores用于设置创建云主机的最大核心数，默认值24
- FrontEnd: 配置文件"frontend.cfg"新增选项max_memory用于设置创建云主机的最大内存容量(GB)，默认值32
- FrontEnd: 配置文件"frontend.cfg"新增选项max_disk用于设置创建云主机的最大磁盘容量(GB)，默认值64
- FrontEnd: 登录页面增加系统错误提示
- FrontEnd: package.json新增参数service.host/service.port用于设置跨域时的后端服务地址
- FrontEnd: 未添加资源节点时进行提示

### 变更

- Cell: 云主机存在快照时，拒绝创建磁盘镜像
- Cell: 允许删除根快照和活动快照
- Cell: 启动时同步网络资源
- Cell: 启动时校验存储卷
- Cell: 磁盘卷锁定时拒绝启动云主机
- FrontEnd: 切换到yarn编译
- FrontEnd: 更新版权日期
- FrontEnd: 仅允许.iso文件上传为光盘镜像
- FrontEnd: 仅允许.qcow2文件上传为磁盘镜像
- FrontEnd: 新建云主机时优化参数配置界面，允许从Frontend接口读取用户自定最大值
- FrontEnd: 新建云主机时，默认选择第一个资源池和系统模板

### 修正

- Core: 搜索云主机时未按创建者和所属组进行过滤
- Cell: 删除快照失败导致模块崩溃
- Cell: 缺少参数导致缩小卷失败

### Added

- Core: Add option 'timeout' to configure file "domain.cfg", default value is 10 seconds
- Cell: Add option 'max_guest' to configure file "data/instance.data", default value is 100
- Cell: Add option 'timeout' to configure file "domain.cfg", default value is 10 seconds
- FrontEnd: Add option "max_cores" to configure file "frontend.cfg", default value is 24
- FrontEnd: Add option "max_memory" in GB to configure file "frontend.cfg", default value is 32
- FrontEnd: Add option "max_disk" in GB to configure file "frontend.cfg", default value is 64
- FrontEnd: Prompt on login page when system error
- FrontEnd: Add service.host/service.port to 'package.json' to configure CORS backend connnection
- FrontEnd: Prompt add first resource node if not available

### Changed

- Cell: Refuse to create disk image when snapshots available
- Cell: Allow to delete root and active snapshot
- Cell: Sync network resources when startup
- Cell: Validate storage volumes when startup
- Cell: Refuse to start instance when volumes locked
- FrontEnd: Migrate to yarn
- FrontEnd: Copyright updated to current year
- FrontEnd: Only allow '.iso' files to upload for media images
- FrontEnd: Only allow '.qcow2' files to upload for disk images
- FrontEnd: Read cores/memory/disk limit via frontend on page of creating instances
- FrontEnd: Optimize core/memory/disk configure in creating page
- FrontEnd: Using first pool by default when creating instance
- FrontEnd: Using first system template by default when creating instance

### Fixed

- Core: Search guests not filter by owner and group
- Cell: crash when delete snapshot failed
- Cell: shrink volume fail when parameter omitted


## [1.3.1] - 2020-02-21

### Added 

- Set auto start in guest detail
- Search and pagination in instance list
- Installer print Nano version when start

### Changed

- Display hosting cell IP instead of name if available

## [1.3.0] - 2020-11-22

### Added

- Manage security policy of instance
- Manage security policy group
- Sync disk/media images from local path
- Create instances with security policy

### Changed

- Optimize the strategy and error output of computing pool allocation
- Optimize the control page of the instance

### Fixed

- Return an explicit error when login with a user does not belong to any group
- Remove from the group when deleting a user
- Return an explicit error when resize disk fail after creating a new image
- Return an explicit error when resize volume fail
- Optimize output of image size in IO Scheduler 
- Consistent checking of instance quantity is not working
- Can't send ctrl+alt+delete in the control page on v1.2.0 
- Images list crashed when no tags available

## [1.2.0] - 2020-04-29

### Added

- Manage cell storage path
- Manage system template
- Reset monitor secret
- Sync instance number when inconsistent
- Add forcibly update option to installer

### Changed

- Optimize interactive on web dialog
- Optimize dashboard display on mobile device
- Using vga as default video device
- Installer check firewalld before installation

### Fixed

- Huge memory occupied when uploading images cause OOM kill in 1.1.0
- Change guest password with wrong user
- Out of memory when monitorint guest resource if no qga installed

## [1.1.0] - 2020-01-02

### Core 1.1.1

#### Added 

- API signature verify
- Add go mod
- Add DNS to API '/address_pools/'(query address pool list)
- Add CreateTime/MAC address to instance/guest

#### Changed

- Call core API via prefix '/api/v1/'
- Change "/media_image_files/:id" to "/media_images/:id/file/"
- Change "/disk_image_files/:id" to "/disk_images/:id/file/"

#### Fixed

- Search guest in an empty cell return a proper result
- Properly return a pending error of instance when get status

### Cell 1.1.1

#### Added

- Add go mod

#### Changed

- Call core API via prefix '/api/v1/'
- Change "/media_image_files/:id" to "/media_images/:id/file/"
- Change "/disk_image_files/:id" to "/disk_images/:id/file/"
- Reset system before initialization change from error to a warning
- Reduce log for DHCP warning
- Network detect interval change to two minutes after established some IP
- Add CreateTime/MAC address to instance

### FrontEnd 1.1.3

#### Added

- Add signature when call Core API
- Add go mod
- Add web_root option to "frontend.cfg" for hosting portal files
- Add cors_enable option to "frontend.cfg" for CORS control

#### Changed

- Call core API via prefix '/api/v1/'
- Change "/media_image_files/:id" to "/media_images/:id/file/"
- Change "/disk_image_files/:id" to "/disk_images/:id/file/"
- A new portal completely was rewritten using React
- Web pages move from 'resource' to 'web_root'

#### Fixed

- Visibility interface broken
- Query logs missing and wrong order    

### Installer 1.1.0

#### Changed

- Change directory of frontend portal files from 'resource' to 'web_root'

## [1.0.0] - 2019-07-14

### Core 1.0.0

#### Added

- Set threshold of CPU/Disk IO/Network

- Batch stop guests

- Automatically synchronize the IP address in the TLS certificate when the IP changes

#### Changed

- Generate module name base on listen address

- URL of guest operates change from '/guest/' to '/guests/'.

- Guests/Images match with owner or group

### Cell 1.0.0

#### Added

- Set threshold of CPU/Disk IO/Network

#### Changed

- Generate module name base on br0

- Move to "github.com/project-nano"

### FrontEnd 1.0.0

#### Added

- Create guests with QoS options

- Modify CPU priority in guest detail

- Set threshold of Disk/Network IO in guest detail

- Batch stop guests

- Enable get/update group visibility

- Record failed login

#### Changed

- URL of guest operates change from '/guest/' to '/guests/'.

- Search guest/media/disk images via session

### Installer 1.0.0

#### Added

- Add 'Update' option to update all installed modules

#### Changed

- Change namespace of the reference library to "github.com/project-nano"


## [0.9.1] - 2019-05-29

### Core 0.9.1

#### Added

- Modify media image

- Get media image

- Query media/disk image filter by owner and group

- Add new API "GET /media_image_search/" for filtering media images by owner and group

#### Changed

- Refactor image server

- The image name is unique in a group

- Results of query disk image sorted by name

- Check image and disk size before clone guest

#### Fixed

- Accumulate CPU usage to a null value

- Return empty data when querying zone status

- Use wrong CPU usage when computing real cell load

### FrontEnd 0.9.1

#### Added

- Get media image

- Query/Add/Remove operate log

- Add version and online manual link to footer

- Add new API "GET /media_image_search/" for filtering media images by owner and group

- Modify disk/media images

- Add operate logs in most pages

#### Changed

- Default landing page change to 'login.html'

- Add group info in session

- Bind resources to current user/group: Create instance/upload&build images

- Media images filtered using the current user and group

- Display the appropriate page according to the menu after login

- Add padding space for sidenav

- Move start/stop/restart/reset instance into nano.js

### Cell 0.8.3

#### Fixed

- Read interface fail due to script code in ifcfg

### Installer 0.1.9

#### Added

- Add 'all' option to install all modules

#### Fixed

- Read interface fail due to script code in ifcfg

## [0.8.2] - 2019-04-04

### Core 0.8.2

#### Fixed

- Media image locked when uploading interrupted

### Cell 0.8.2

#### Fixed

- Enable Cloud-Init after resetting system image

### FrontEnd 0.8.2

#### Fixed

- Prompt an invalid dialog when removing ranges from an address pool

- Logout when deleting address pool/computing pool/storage pool

- Prompt an invalid dialog when removing a cell from computing pool

- Logout when deleting a media/disk image

- Logout when modify user/password

- Logout when deleting user

- Logout when removing role/group/group member


## [0.8.1] - 2019-03-26

### Core 0.8.1

#### Added

- Modify guest name

- Batch creating/deleting guest

#### Changed

- Adapt to new runnable implement

- Locate cert files of image server base on the binary path


### Cell 0.8.1

#### Added

- Rename guest

#### Changed

- Migrate bridge configure from interface

- Adapt to new runnable implement


### FrontEnd 0.8.1

#### Added

- Check resource path

- Enable batch creating and deleting/modify guest name/modify image info

- Batch creating/deleting guest

- Modify user password

- Modify guest name

#### Changed

- Locate resource using ABS path

- Adapt to new runnable implement

- Verify guest name before submit creating request

- Navigation menu change to the sidebar

- Update chartjs to v2.8


## [0.7.1] - 2019-01-03

### Core 0.7.1

#### Added

- System start time when query zone status

- Reset guest system

### Cell 0.7.1

#### Added

- "legacy" option of system version

- Reset guest system

- Sync storage option when compute pool available

### FrontEnd 0.7.1

#### Added

- Role/Group/User management

- Session management

- Invoke system initial page when no user configured

- Enable reset system

- Add "legacy system" option when create new instance

- Add uptime to dashboard.html

### RPMS

#### Changed

- Update all rpms base on CentOS 7.6(1810)

## [0.6.1] - 2018-11-30

### Core 0.6.1

#### Added

- Address pool management: query/create/modify/delete

- Address range management: add/remove

- Instance address allocate/migrate

- Allocated address in instance status

### Cell 0.6.1

#### Added

- Support assigned network address of instance

- Enable distributed DHCP service for MAC bound

- Configure template for different OS version

- Optimize mouse position using tablet input

- Disable DHCP service in default network when startup

### FrontEnd 0.6.1

#### Added

- Redirect address pool/range API

- Addess pool/range managment page

#### Changed

- Address pool option when creating/modifing compute pool

### Installer 0.1.8

#### Added

- Enable DHCP port for cell

#### Changed

- Disable NetworkManager before link bridge to prevent ssh disconnection

- Migrate bridge configure from interface

## [0.5.1] - 2018-11-3

### Core 0.5.1 

#### Added

- Enable/Disable cell

- Enable failover in compute pool

- Migrate instance

#### Changed

- Optimize load balance algorithm considering both real-time load and instances configured when choosing cell for allocation.

- Sort instance list by lexicographic order

### Cell 0.5.1

#### Added

- Attach/Detach instances

- Add 'qcow2' suffix to volume/snapshot files

- Set hostname when using CloudInit module

- Check the default route when startup

#### Changed

- Randomize allocation of the monitor port

- Determine system/admin name of the guest by version when creating an instance

### FrontEnd 0.5.1

#### Added

- Multi-language support

- Enable/Disable cell

- Enable failover option in compute pool

- Migrate instance

#### Changed

- Optimize console output when starting module

### Installer 0.1.7

#### Added

- Check default route

## [0.4.2] - 2018-10-11

### Core 0.4.2

#### Fixed

- result.Error output message

### Cell 0.4.2

#### Added

- Synchronize allocated network ports to instance configures

#### Fixed

- Compatible with local storage config file of the previous version

## [0.4.1] - 2018-10-2

### Core 0.4.1 

#### Added

- Storage Pool management: Create/Delete/Modify

- NFS storage backend supported

- Allow choosing storage pool when creating/modifying compute pool

- Synchronize storage configure when cell joined or added

- Add storage mount status when getting cell status

- Check duplicate instance name in a pool when creating a guest

- Mark instance status to lost when cell disconnected

- Notify cell to detach storage when removed from pool

#### Fixed

- Improper instance count when instance deallocated

- Task put a message to closed proxy channel causing panic

- Task put a message to deallocated proxy session causing panic

### Cell 0.4.1

#### Added

- Support NFS storage pool

- Report share storage(NFS) mount status

- Support volume/snapshot save on shared storage

- Create instance metadata when using shared storage

- Automount shared storage when cell start or added to compute pool

#### Fixed

- Snapshot files left when delete volumes

- Try recover stub service when stop module

### FrontEnd 0.4.1

#### Added

- Support storage pool management

- Modify compute pool

- Get compute cell info

- Standalone google materialize icons

- Mark instance lost status when cell stop/disconnected

- Add image id in list

#### Fixed

- No response to click start or insert media button when no media available.

- Auto fresh page become slower after a long time running

- Deleted instance count in the dashboard

- Output message without clear previous info in the list

### Installer 0.1.6

#### Changed

- Install nfs-client/semanage for cell

- Ask if continue when installing fail


## [0.3.1] - 2018-8-29

### Core 0.3.1

#### Added

- Insert/Eject media in instance

- Add instance create time

- Add create and modify time of images

- Snapshot management: create/restore/delete/query/get

#### Fixed

- Wrong instance name sent to cell when create a new guest

### Cell 0.3.1

#### Added

- Snapshot management: create/delete/restore/get/query

- Storage create time of guest

- Inject/eject media in running instance

- Lock volumes when running disk operates

#### Fixed

- Get instance status sync status without notify core


### FrontEnd 0.3.1


#### Added

- Create time of Instance

- Create/modify time of Image

- Snapshot management: create/ delete / revert

- Insert / eject media image

#### Changed

- Enable instance funtions in instance monitor page

- Change cpu/memory usage to bar chart in dashboard/instance monitor

- Open new tab for monitor/snapshots/details of instances list


## [0.2.3] - 2018-8-17

### Core 0.2.3

- Support initialize guest after created using Cloud-Init in NoCloudMode

- Enable guest system version/modules configure

- Enable change admin password/create new admin/auto resize&mount disk when ci module enabled (cloud-init cloud-utils required in guest)

- Qualify instance/user/group/image name (only '0~9a~Z-' allowed)

### Cell 0.2.3

- Support initialize guest after created using Cloud-Init in NoCloudMode

- Enable guest system version/modules configure

- Enable change admin password/create new admin/auto resize&mount disk when ci module enabled (cloud-init cloud-utils required in guest)

- Add listen port TCP: {cellIP}:25469 for Cloud-Init initiator


### FrontEnd pages

- Support choose installed module when cloning from an image

- Enable change admin password/ create new admin/ disk auto resize/ data disk mount when Cloud-Init module installed

- Add auto fresh in instances.html

- Optimize instances/cells auto refresh, interval reduced to 5 seconds

- Fixed: multiple image names displayed when starting with media


## [0.2.2] - 2018-8-6

### Core 0.2.2

- Stable sorted result of instance/image/cell/pool list

### Cell 0.2.2

- Enable KVM instead of TCG of QEMU, boost performance when VT-x/AMD-v enabled

- Using the IDE system disk if the system of an instance is "windows".

- Don't save NetworkAddress of Instance

- Avoid response channel block after timeout event invoked

- Fixed: panic when try to notify the Resize/Shrink tasks

### FrontEnd resource

- Add auto fresh switch in cell/instance list

### Installer 0.1.3

- modify user/group in /etc/libvirt/qemu.conf before start service

## [0.2.1] - 2018-07-31

### Core 0.2.1

- Modify Cores/Memory/Disk Size

- Shrink guest volume

- Set/Get user password

- Add "system" property in guest

- Fixed: a newly uploaded disk image cannot use in cloning

### Cell 0.2.1

- Modify Cores/Memory/Disk Size

- Shrink guest volume

- Set/Get user password

- Add "system" property in guest

### FrontEnd 0.2.1

- Doc: Modify core/memory/disk size, shrink disk, set/get password

- Forward Request: Modify core/memory/disk size, shrink disk, set/get password

- Add guest modify page: instance_detail.html


## [0.1.3] - 2018-07-25

### Core 0.1.3

- Handle instance address changed event

- API redirect disk image requests

- Ignore offline cells when compute score

- Forward create disk image request when no target guest specified

- Support form uploading

- Fixed: instance internal and external address

### Cell 0.1.4

- Resize guest disk when clone finished

- Compute instance CPU usage properly

- Get IP address for started instance

- Notify Core module when instance ip detected

- Fixed: Internal instance address not send to Core module

### FrontEnd 0.1.2

- Version output

- Disk image upload and download

- Add auto refresh to compute_cells.html and instance_list.html



## [0.1.2] - 2018-07-21

### Core

- gracefully disconnect when module stop

- add version output on the console

### Cell

- add version output on the console

- add qemu-agent channel in guest

- fix instance memory usage monitor

- try to reconnect when core disconnected

- gracefully disconnect when module stop

- bug fixed: random MAC not properly generated
