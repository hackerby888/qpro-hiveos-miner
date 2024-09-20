# QubicMine.Pro | HiveOs Miner

The qpro-miner HiveOs .
Use URL in HiveOs flight sheet:
<br>
## :warning: HiveOs Mandatory Installation Instructions

-   The CPU where you run the Client must support AVX2 or AVX512 CPU instructions
    `cat /proc/cpuinfo | grep avx2`(check if `avx2` is in the result)
-   To run the Qubic miner, you need the beta version of HiveOS.
    `/hive/sbin/hive-replace --beta --yes`
-   Cuda 12+ drivers (525+)
-   Cuda 12 for 1000 series must be 535+
    `nvidia-driver-update 535.146.02` (or newer)
-   RAM >= 16Go improves CPU it/s
-   Higher RAM frequencies improves CPU it/s
-   Do not overload your CPUs with threads, instead, aim to find the sweetpoint

## :warning: Checking and Upgrade Tutorial
- The CPU where you run the Client must support AVX2 or AVX512 CPU instructions.
```sh
cat /proc/cpuinfo | grep avx2
```
(check if `avx2` is in the result)
- RAM should be >= 16GB to improve CPU performance.
- Higher RAM frequencies improve CPU performance.
- Do not overload your CPUs with threads; instead, aim to find the sweet spot.

- To run the Qubic miner, you need the beta version of HiveOS. Run:
```sh
/hive/sbin/hive-replace --beta --yes
```
- You need GLIBC version 2.34 or higher. During the installation process, select "Yes" and press Enter.
Run the following commands:
```sh
apt update && echo "deb http://cz.archive.ubuntu.com/ubuntu jammy main" >> /etc/apt/sources.list && apt update && apt install unzip g++ gcc g++-11 -y && apt install libc6 -y && sed -i '/deb http:\/\/cz\.archive\.ubuntu\.com\/ubuntu jammy main/d' /etc/apt/sources.list && apt update
```

**For NVIDIA cards:**
- Cuda 12+ drivers (525+) 
- Cuda 12 for 1000 series must be 535+ (or newer)
```sh
nvidia-driver-update 535.146.02
```
- For 4000 series use version 550+
```sh
nvidia-driver-update 550.54.14
```

### GPU mining:

Extra config arguments exemple:

**Sample Configuration for NVIDIA GPU's**
![Flight Sheet CPU](/img/gpu.png)

```
--gpu --wallet PTXKGDSPQNDTBFRNLTRPKVZAEEMCWFBUBSMDYKMYSBYMYHJWLHURNIFFZSPE

```

### CPU mining:

Extra config arguments exemple:
![Flight Sheet CPU](/img/cpu.png)

```
--cpu -i avx2 -t 4 --wallet PTXKGDSPQNDTBFRNLTRPKVZAEEMCWFBUBSMDYKMYSBYMYHJWLHURNIFFZSPE
```

## :wrench: Hive Os Settings

### Miner Configuration

-   **Miner name:** Automatically filled with the installation URL.
-   **Installation URL:** `https://github.com/hackerby888/qpro-hiveos-miner/releases/tag/v1.0.7`
-   **Hash algorithm:** qubic.
-   **Wallet and worker template:** %WORKER_NAME%.
-   **Pool URL:** ws.qubicmine.pro.
-   **Pass:** Not used.
-   **Extra config arguments:** Read at https://qubicmine.pro/get-started.

### Recommended GPU overclocks :

**Medium**  
3000 series `nvtool --setcoreoffset 250 --setclocks 1500 --setmem 5001`  
4000 series `nvtool --setcoreoffset 250 --setclocks 2400 --setmem 5001`  
**High**  
3000 series `nvtool --setcoreoffset 200 --setclocks 1600 --setmem 7000 --setmemoffset 2000`  
4000 series `nvtool --setcoreoffset 200 --setclocks 2900 --setmem 7000 --setmemoffset 2000`
