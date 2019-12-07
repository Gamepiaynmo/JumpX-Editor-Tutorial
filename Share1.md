# 关于ini的一点发现

## ini里部分字段的参数以及效果

- Mode
    - Life ：持续时间类型 需要指定Life=持续时间（毫秒）
    - WaitAllDead ：等待所有特效播放完毕
    - Loop ：循环 Loop=循环次数（forever可以永久持续）Life=持续时间(毫秒)
- Model ：使用的模型路径
- Num ：总特效个数 最多4
- Scale ：缩放float值，格式1.0f
- ScaleS ：东向缩放
- ScaleE ：南向缩放

- Bind ：特效绑定点
    - LeftHand 左手 骨骼名字（Bip001 L Finger11）
    - RightHand 右手 骨骼名字（Bip001 R Finger11）
    - Body 身体 骨骼名字（Bip001 Spine3）
    - Foot 脚下 就是贴着地面
    - Spray 貌似没有效果，出现在地面上
    - Bone 绑定到指定的骨骼上 Bone=骨骼名

- Radius 半径，貌似无用

- Delay 等待时间，ini激活后过多久这个特效才出现（毫秒）

- DeadRenderTime ：死亡渲染时间（毫秒）

- FadeOutTime ：淡出时间（毫秒）

- RotateTogether ：是否一起旋转 0 or 1

- RotCorrect ：旋转补正

- UseBindEffectScale ：使用绑定效果比例 0 or 1 不写则是0

- CameraDirOffset ：摄像机偏移

- Action 
    - Trace ：发射出去的效果
    - Spray ：创建时朝向绑定单位面向方向，之后不跟随移动和旋转
    - Follow ：创建时朝向绑定单位面向方向，之后跟随移动但不跟随旋转
    - Followpos ：创建时朝向x轴方向，之后跟随移动但不跟随旋转
    - FullScreen ：全屏特效，默认在（0，0）点显示

- ActionTime ：没有发现效果

- AlwayDisplay ：总是显示 0 or 1

- DisapearAfterAction ：行动后消失 0 or 1

- RenderAddons ：渲染插件（要在main里加）
    - 1 同4
    - 2 残影
        - RenderAddonsParameter0  影子的长度，1-9数字越高越长 
        - RenderAddonsParameter1  影子个数，10等于1个影子 
        - RenderAddonsParameter2  开始颜色 0-ffffff RGB颜色，填写时需要把值转换为10进制
        - RenderAddonsParameter3  结束颜色 0-ffffff RGB颜色，填写时需要把值转换为10进制
        - RenderAddonsKey  无效
        - RenderAddonsTimes  特效持续时间（毫秒）
    - 3 无效
    - 4 表面渲染 （双面的网格只会有一面生效）
        - RenderAddonsParameter0 整体透明度 0-255
        - RenderAddonsParameter1 颜色 0-ffffff RGB颜色，填写时需要把值转换为10进制
        - RenderAddonsKey  表面渲染的贴图路径
        - RenderAddonsTimes 特效持续时间（毫秒）
    - 5 同4

- CameraShakeType 摄像头震动类型
    - Normal 普通类型
    - HorizontalShake 水平震动
    - VerticalShake 垂直震动

    - MaxShakeWaveRange 最大震动波动半径0-1
    - MinShakeWaveRange 最小震动波动半径0-1
    - MaxShakeRange 最大震动半径0-1
    - MinShakeRange 最小震动半径0-1
    - ShakeKeepTime 震动持续时间
    - ShakeStartTime 震动等待开始时间
    - ShakeStep 震动步骤 （没有影响）
    - ShakeAttenuation 震动衰减（0-1正负都一样，太大震动会越剧烈）
    - AttenuationSpeed 震动衰减速度
    - AttenuationTime 震动衰减时间
    - StepAttenuationSpeed 步骤衰减速度
    - StepAttenuationTime 步骤衰减时间

- Screen 是否是UI特效 0 or 1 默认为0
    - screenX UI特效的X坐标
    - screenY UI特效的Y坐标，坐标轴原点在屏幕左上角

- TrackType
    - Line ：没有什么效果
    - Para ：同上
    - ParaHight ：可能和渲染插件的启用有关，等待后续测试

- Link ：是否是连线特效
    - Pos2 模型的B2点会连在Bind指定点上

- TileU ：是否U向缩放

- TileV ：是否V向缩放

- IgnoreMaster ：忽略大师，猜测是忽略其他的代码

- NewSound ：给特效添加音效event:/音效路径

- Delegatesound :代表声音，效果不明

- Volume ：音量，但是貌似没有效果	

- MaxRange ：最大范围，也没发现效果