#BLE 4.0随笔

--

####一、蓝牙常见名称和缩写

- BLE：(Bluetooth low energy)蓝牙4.0设备因为低耗电
- Central：中心设备，发起蓝牙连接的设备(一般是指手机)
- Peripheral：外设，被蓝牙连接的设备(一般是运动手环)
- Service and Characteristic：服务和特征，每个设备会提供服务和特征，类似于服务端的API，但是结构不同，每个设备会有很多服务，每个服务中包含很多特征，这些特征的权限一般分为读(read)，写(write)，通知(notify)几种，就是我们连接设备后具体需要操作的内容
- Description：描述，每个Characteristic可以对应一个或者多个Description用于描述Characteristic的信息或属性