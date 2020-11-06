## Hyper-V下嵌套虚拟化配置

#### 步骤
1. 需要以管理员方式打开PowerShell
2. Get-VM命令查看虚拟机
3. Get-VMProcessor -VMName ubuntu查看虚拟机ExposeVirtualizationExtensions，false表示未使能
4. Set-VMProcessor -ExposeVirtualizationExtensions $true -VMName ubuntu即可配置嵌套虚拟化，此时在虚拟机内可以看到/dev/kvm
