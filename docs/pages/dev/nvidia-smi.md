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

Query CLOCK-related status

```bash
nvidia-smi -q -d CLOCK
```

## Set GPU Clock Speed

Set lower and upper bound for NVIDIA GPU Clock
- `-lgc` for lock gpu clocks

```bash
sudo nvidia-smi -lgc 200,1200
```

Reset NVIDIA GPU Clock
- `-rgc` for reset gpu clocks

```bash
sudo nvidia-smi -rgc
```

## Set Power Limits

Specifies maximum power limit (pl) in watts

```bash
sudo nvidia-smi -pl 120
```

## Specific Queries

```bash
nvidia-smi --query-gpu=index,gpu_name,utilization.gpu,temperature.gpu,memory.total,memory.used,memory.free --format=csv
```

## Install & Use `nvtop`

- NVIDIA GPU monitoring tool [nvtop](https://github.com/Syllo/nvtop)

Install

```bash
sudo apt install nvtop
```

Usage

```bash
nvtop
```