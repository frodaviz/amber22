# amber22
Amber22 and AmberTools23 on docker container

## Build
With cuda nvidia

## Run

docker run -it --rm --gpus all -v /home/irgb/mutation/:/work amber22_builded /opt/amber22/bin/pmemd.cuda -v

## Test

Tested on workstation with

Linux mikasa.irgb.local 6.2.0-37-generic #38~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC x86_64 x86_64 x86_64 GNU/Linux
0000:01:00.0 VGA compatible controller: NVIDIA Corporation TU117GL [T1000 8GB] (rev a1)

Tested on server with 

Linux eva01.irgb.local 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC x86_64 x86_64 x86_64 GNU/Linux
0000:17:00.0 VGA compatible controller: NVIDIA Corporation GA102GL [RTX A5000] (rev a1)

+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.147.05   Driver Version: 525.147.05   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA RTX A5000    Off  | 00000000:17:00.0 Off |                  Off |
| 49%   75C    P2   226W / 230W |    462MiB / 24564MiB |     97%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1462      G   /usr/lib/xorg/Xorg                  4MiB |
|    0   N/A  N/A   1583605      C   /opt/amber22/bin/pmemd.cuda       454MiB |
+-----------------------------------------------------------------------------+

