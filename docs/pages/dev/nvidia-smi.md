# NVIDIA GPU Driver Commands

## Check GPU status

Check status overview

```bash
nvidia-smi
```

Query full status log

```bash
nvidia-smi -q
```

Query all Clock-related status

```bash
nvidia-smi -q -d CLOCK
```

## Set GPU Clock Speed

Set lower and upper bound for NVIDIA GPU Clock

- `-lgc` stands for lock gpu clocks

```bash
sudo nvidia-smi -lgc 200,1200
```

Reset NVIDIA GPU Clock to default value

- `-rgc` stands for reset gpu clocks

```bash
sudo nvidia-smi -rgc
```

## Set Power Limits

Specifies maximum power that the GPU can draw

- `pl` stands for power limit 
- Unit: Watts

```bash
sudo nvidia-smi -pl 120
```

## Specific Queries

Example: 

To query specific information such as:

- index
- gpu_name
- utilization.gpu
- temperature.gpu
- memory.total
- memory.used
- memory.free

You may execute the following command:

```bash
nvidia-smi --query-gpu=index,gpu_name,utilization.gpu,temperature.gpu,memory.total,memory.used,memory.free --format=csv
```

- The list of valid properties can be obtained using `nvidia-smi --help-query-gpu`
- The argument `--format=csv` is always required.


## NVIDIA GPU Monitoring Tools

- [**nvtop**](https://github.com/Syllo/nvtop)
- [**nvitop**](https://github.com/XuehaiPan/nvitop)

### Install & Use `nvtop`

Install

```bash
sudo apt install nvtop
```

Usage

```bash
nvtop
```