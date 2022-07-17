---
title: "Error404 Circuit Simulator"
date: 2020-06-16T20:28:00.000Z 
extra:
    featured: true
    link: https://github.com/neeldug/404CircuitSim
    image: /media/ISO_CPP_Logo.svg
description: 📊 A simple command-line utility for simulating analog circuits with multiple supported components. 
taxonomies:
  tags:
    - C++
    - Python
---

### Circuit Simulator

A CLI package, built with the intention to have a simpler interface of LTSpice.

Built for end of year 1 group project.

Provides support for:

- Resistors
- Inductors
- Capacitors
- Diodes

#### Usage

`$ simulator -i file [ -ch ] [ -o dir ] [-p list] [ -s path ] [ -f format ]`

Options:

* `-i <path>`          : Supply path to input netlist
* `-o <path>`          : Supply path to output directory
* `-f <format>`        : Specify output format, either `csv` or `space`
* `-p <list>`          : Generates interactive plot with space separated list of columns to view
* `-s <path>`          : Saves interactive plot as HTML file at specified location
* `-c`                 : Shows names of columns in output file, blocks -p and -s i.e. doesn't plot/save result
* `-h`,                : Shows help information

Examples usages:

Plot Specific Columns:
`simulator -i test.net -p 'V(N001) V(N002)'`

Plot All Columns and save result as interactive HTML:
`simulator -i test.net -p '' -s result.html`

Generate result and check names of columns in netlist:
`simulator -i test.net -c`

#### Quick Installation

Clone the repository and perform the following:

```bash
cd build
./install.sh
```
