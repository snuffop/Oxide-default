---
id: 20251021131001--miniconda-install
aliases:
  - Miniconda Install
tags:
  - resource
  - tipjar
date: Tuesday October 21st 2025
path: Resource/TipJar
title: Miniconda Install
---

## Miniconda Install Highlights

### Links

- [Documentation](https://www.anaconda.com/docs/getting-started/miniconda/install#linux-2)

## Install miniconda

Install

``` bash
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

Activate

``` bash
source ~/miniconda3/bin/activate
```

Init

``` bash
conda init --all
```

## Conda - Forge Install

### Activate the environment (replace 'myenv' with yours)

``` bash
conda activate myenv
```

### Add conda-forge globally or per-env

``` bash
conda config --add-channels conda-forge
```

### Ensure conda-forge has highest priority

``` bash
conda config --set channel_priority strict
```

### Optional: confirm configuration

``` bash
conda config --show channels
```

# Footer

