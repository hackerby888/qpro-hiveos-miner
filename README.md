# QubicMine.Pro | HiveOs Miner

The qpro-miner HiveOs .
Use URL in HiveOs flight sheet:
<br>
[https://github.com/hackerby888/qpro-hiveos-miner/releases/download/v1.9.7/qprominer-1.9.7b.tar.gz](https://github.com/hackerby888/qpro-hiveos-miner/releases/download/v1.9.7b/qprominer-1.9.7b.tar.gz)

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

**For AMD cards:**
- Install version 5.7.3 drivers using the command:
```sh
amd-ocl-install 5.7 5.7
```
- Install the libamdhip64 library. 
Run the following commands:
```sh
cd /opt/rocm/lib && wget https://github.com/Gddrig/Qubic_Hiveos/releases/download/0.4.1/libamdhip64.so.zip && unzip libamdhip64.so.zip && chmod +rwx /opt/rocm/lib/* && rm libamdhip64.so.zip && cd / && ldconfig
```
<br>

> [!IMPORTANT]
> AMD Version was tested with hiveos version `6.1.0-hiveos` and AMD drivers `5.7.3`. Please take this as minimum requirenments.

### GPU mining:

Extra config arguments exemple:

**Sample Configuration for AMD GPU's**
![Flight Sheet CPU](/img/amd.png)

```
"trainer": {"gpu":true,"gpuVersion": "AMD"}
"payoutId":"YOURWALLET"
"alias":"YOURALIAS"
```

**Sample Configuration for NVIDIA GPU's**
![Flight Sheet CPU](/img/cuda.png)

```
"trainer": {"gpu":true,"gpuVersion": "CUDA12"}
"payoutId":"YOURWALLET"
"alias":"YOURALIAS"
```

### CPU mining:

Extra config arguments exemple:
![Flight Sheet CPU](/img/cpu.png)

```
"cpuOnly":"yes"
"amountOfThreads":24
"payoutId":"YOURWALLET"
"alias":"YOURALIAS"
"trainer": {"cpu":true,"cpuVersion": "GENERIC"}
```

## :wrench: Hive Os Settings

### Miner Configuration

-   **Miner name:** Automatically filled with the installation URL.
-   **Installation URL:** `https://github.com/hackerby888/qpro-hiveos-miner/releases/download/v1.9.7b/qprominer-1.9.7b.tar.gz`
-   **Hash algorithm:** Not used. Auto set.
-   **Wallet and worker template:** Not used. Type anything.
-   **Pool URL:** Use `https://mine.qubicmine.pro/` for the pool.
-   **Pass:** Not used.
-   **Extra config arguments:** Each line is merged into `qubicmine.json`.

### Recommended GPU overclocks :

**Medium**  
3000 series `nvtool --setcoreoffset 250 --setclocks 1500 --setmem 5001`  
4000 series `nvtool --setcoreoffset 250 --setclocks 2400 --setmem 5001`  
**High**  
3000 series `nvtool --setcoreoffset 200 --setclocks 1600 --setmem 7000 --setmemoffset 2000`  
4000 series `nvtool --setcoreoffset 200 --setclocks 2900 --setmem 7000 --setmemoffset 2000`

### Extra config arguments Box (options):

| Setting | Description                                                                                                                                                                                                                                  |
| ---- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ```"payoutId":``` | This is the wallet address you want to get token payout for your found solutions.                                                                                                                                                                        |
| ```"hugePages":nnnn``` | Depending on your environment you might want to enable huge pages. This can increase your iterations per second. The trainer will tell you what is the optimal setting when it detects a wrong value. The number depends on the number of threads: nb_threads * 52 (e.g., 16 * 52 = 832). If trainer is unstable please remove. |
|  ```"overwrites": {"AVX512": false}``` | Disable AVX512 and enforce AVX2 (AVX Intel CPU not working)                                                                                                                                                                                  |
| ```"overwrites": {"SKYLAKE": true}```  | Enforce SKYLAKE (AVX Intel CPU not working)                                                                                                                                                                                                  |
| ```"trainer": {"gpu": true, "gpVersion": "AMD"}```  | Enforce AMD                                                                                                                                                                                                  |
<br>
