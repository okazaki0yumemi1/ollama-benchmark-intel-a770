# ollama-benchmark on Intel Arc A770 dGPU

Got this script from tabletuser-blogspot/ollama-benchmark (https://github.com/tabletuser-blogspot/ollama-benchmark).

# My Setup

dPGU: two Intel Arc A770 Limited Edition with 16Gb VRAM. No overclock, no tuning, PCI-E 3.0x16 electrical.

OS: Ubuntu 24.10, Kernel 6.11.

Motherboard + CPU: Asrock X399 + Threadripper 1950x. 

Keep in mind that I probably messed up something during install and because of that I have lower performance than other persons.


# My Results

I ran the script 5 times with some models I had and got the following results:

|Model name|Average Evaluation Rate|Power Usage (1st card + 2nd card)|Memory Usage (1st card + 2nd card)|
|:--|:--|:--|:--|
|deepseek-r1:14b|16.65 tokens/second|81W + 86W|5157 MiB + 5625 MiB|
|phi4:14b|19.08 tokens/second|90W + 92W|5749 MiB + 5732 MiB|
|qwen3:4b|23.01 tokens/second|70W + 71W|2016 MiB + 2382 MiB|
|qwen3:30b*|11.23 tokens/second|73W + 68W|9634 MiB + 9425 MiB| 

*qwen3:30b - got 4 tokens/second on 3rd and 4th run, decided to stop the benchmark.

For the VRAM usage and power consumption I was using these commands:
```
xpu-smi stats -d 0
# for the first GPU and 
xpu-smi stats -d 1
# for the second GPU.
```
