# QubicMine.Pro | HiveOs Miner

The qpro-miner HiveOs .
Use URL in HiveOs flight sheet:
<br>
https://github.com/hackerby888/qpro-hiveos-miner/releases/download/v1.9.6b/qprominer-1.9.6b.tar.gz

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

<br>

> [!IMPORTANT]
> AMD Version was tested with hiveos version `6.1.0-hiveos` and AMD drivers `5.7.3`. Please take this as minimum requirenments.
> AMD Version is currently only allowed in `qubic.li CPU/GPU Mining (Fixed Reward 85%)`

### GPU mining:

Extra config arguments exemple:

**Sample Configuration for AMD GPU's**
![Flight Sheet CPU](/img/gpu_amd.png)

```
"trainer": {"gpu":true,"gpuVersion": "AMD"}
"payoutId":"YOURWALLET"
"alias":"YOURALIAS"
```

**Sample Configuration for NVIDIA GPU's**
![Flight Sheet CPU](/img/gpu_cuda.png)

```
"trainer": {"gpu":true,"gpuVersion": "CUDA12"}
"payoutId":"YOURWALLET"
"alias":"YOURALIAS"
```

### CPU mining:

Extra config arguments exemple:
![Flight Sheet CPU](/img/new_cpu.png)

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
-   **Installation URL:** `https://github.com/hackerby888/qpro-hiveos-miner/releases/download/v1.9.6b/qprominer-1.9.6b.tar.gz`
-   **Hash algorithm:** Not used, leave as `----`.
-   **Wallet and worker template:** Not used.
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
