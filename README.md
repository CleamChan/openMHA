[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4569575.svg)](https://doi.org/10.5281/zenodo.4569575)
![GitHub](https://img.shields.io/github/license/HoerTech-gGmbH/openMHA)

# openMHA

[Open Master Hearing Aid (openMHA)](https://www.openmha.org)

DOI:[10.5281/zenodo.4569575](https://doi.org/10.5281/zenodo.4569575)

Current release: 4.18.0 (2024-05-16)

## 中文项目描述

openMHA（Open Master Hearing Aid）是一个面向助听算法研究与原型验证的开源平台。  
从工程结构看，本仓库主要由以下几部分组成：

* **核心框架与命令行应用**：位于 `mha/` 目录，提供实时音频处理运行时、插件加载机制和配置驱动的处理流程。
* **算法插件与处理链能力**：包含校准、波束形成、噪声抑制、动态范围压缩、反馈抑制等助听器关键模块，可按配置文件组合成完整处理链。
* **工具链与接口**：`mha/tools/` 下提供 Python、Java、Matlab/Octave 相关控制与集成工具，以及打包、拟合规则封装等实用脚本。
* **示例与参考实现**：`examples/` 与 `reference_algorithms/` 提供可复现实验配置，便于快速上手、复现实验论文并开展二次开发。
* **第三方依赖封装**：`external_libs/` 收录部分外部库与构建配置，用于支持跨平台构建和特定功能扩展。

整体上，openMHA 的定位是：在“研究可复现性 + 实时处理能力 + 工程可扩展性”之间取得平衡，帮助研究者和开发者以较低成本实现从算法想法到可运行助听原型的落地。

## Content of the openMHA

The software contains the source code of the openMHA Toolbox library, of the
openMHA framework and command line application, several tools to operate openMHA and of a selection of algorithm
plugins forming a basic hearing aid processing chain featuring

* calibration
* bilateral adaptive differential microphones for noise suppression [1]
* binaural coherence filter for feedback reduction and dereverberation [2]
* multi-band dynamic range compressor for hearing loss compensation [3]
* spatial filtering algorithms:
    * a delay-and-sum beamformer
    * a MVDR beamformer [4]
* single-channel noise reduction [5]
* resampling and filter plugins
* STFT cyclic aliasing prevention
* adaptive feedback cancellation [6]
* probabilistic sound source localization [7]

See below for a list of available reference implementations.

## Citation in publications

In publications using openMHA please use the DOI assigned to this Github repository,
[10.5281/zenodo.4569575](https://doi.org/10.5281/zenodo.4569575),
and cite the following open-access publication:


Hendrik Kayser, Tobias Herzke, Paul Maanen, Max Zimmermann, Giso Grimm, and Volker Hohmann,
Open community platform for hearing aid algorithm research: open Master Hearing Aid (openMHA),
SoftwareX, Volume 17, 2022, 100953, ISSN 2352-7110, [DOI: 10.1016/j.softx.2021.100953](https://doi.org/10.1016/j.softx.2021.100953).


For individual algorithms, please also refer to the plugin documentation and the 
list of publications at the end of this README.

## Installation

For installation instructions for Linux, Windows and macOS, please refer
to the instructions in file INSTALLATION.md.

We also provide SD card images for Beaglebone Black with the Cape4all
sound card here: http://mahalia.openmha.org/.

## Usage instructions:

Please follow our getting-started guide:
http://www.openmha.org/docs/openMHA_starting_guide.pdf

Our user forum is found here:
https://forum.openmha.org/

## Known issues
### macOS
* There are some known issues with Octave under macOS.  The openMHA GUI may
  not work correctly with Octave. As an alternative Matlab can be used.

## Proprietary fitting rules
It is possible to fit a dynamic compressor in openMHA with the
commercial hearing aid prescription rules *DSLmio 5* and *NAL NL2*.

The software libraries implementing these rules must be obtained from
their respective authors.  The openMHA team provides wrappers around
these libraries which for legal reasons are not distributed as part of
openMHA but as optional extras.

Please refer to files README_NALNL2.md and README_DSLmio5.md for more
information.

## Reference algorithms

A collection of openMHA configuration files that implement signal
processing algorithms for hearing aids as they were used in the 
following publications are available in the *reference_algorithms* directory:

Baumgärtel, R. M., Krawczyk-Becker, M., Marquardt, D., Völker, C.,
Hu, H., Herzke, T., Coleman, G., Adiloğlu, K., Ernst, S. M., Gerkmann, T., 
Doclo, S., Kollmeier, B., Hohmann, V., & Dietz, M. (2015). Comparing 
Binaural Pre-processing Strategies I: Instrumental Evaluation. Trends 
in hearing, 19.
https://doi.org/10.1177/2331216515617916

and

Hendrikse, M. M. E., Grimm, G., & Hohmann, V. (2020). Evaluation of
the Influence of Head Movement on Hearing Aid Algorithm Performance
Using Acoustic Simulations. Trends in Hearing, 24, 1–20. 
https://doi.org/10.1177/2331216520916682

A database that can be utilized to reproduce the signals used in the latter
study is available under: https://doi.org/10.5281/zenodo.3621282.
 
Available methods:

* Single-channel noise reduction
* Binaural coherence filter
* Adaptive MVDR beamformer
* Binaural beamformer
* Bilateral adaptive differential microphones
* Delay-and-subtract beamformer

For references and more information see file README.md in the
 *reference_algorithms* directory.

## References for individual algorithms

[1] Elko GW, Pong ATN. A Simple Adaptive First-order Differential
Microphone. In: Proceedings of 1995 Workshop on Applications of Signal
Processing to Audio and Accoustics; 1995. p. 169–172.

[2] Grimm G, Hohmann V, Kollmeier B. Increase and Subjective
Evaluation of Feedback Stability in Hearing Aids by a Binaural
Coherence-based Noise Reduction Scheme. IEEE Transactions on Audio,
Speech, and Language Processing. 2009;17(7):1408–1419.

[3] Grimm G, Herzke T, Ewert S, Hohmann V. Implementation and
Evaluation of an Experimental Hearing Aid Dynamic Range Compressor
Gain Prescription. In: DAGA 2015; 2015. p. 996–999.

[4] Adiloğlu K, Kayser H, Baumgärtel RM, Rennebeck S, Dietz M, Hohmann
V. A Binaural Steering Beamformer System for Enhancing a Moving Speech
Source. Trends in Hearing. 2015;19:2331216515618903

[5] Gerkmann T, Hendriks RC. Unbiased MMSE-Based Noise Power
Estimation With Low Complexity and Low Tracking Delay. IEEE
Transactions on Audio, Speech, and Language
Processing. 2012;20(4):1383–1393.

[6] Schepker H, Doclo S, A semidefinite programming approach to
min-max estimation of the common part of acoustic feedback paths in
hearing aids. IEEE Transactions on Audio, Speech, and Language
Processing. 2016;24(2):366-377.

[7] Kayser H, Anemüller J, A discriminative learning approach to
probabilistic acoustic source localization. In: International Workshop
on Acoustic Echo and Noise Control (IWAENC 2014); 2014. p. 100–104.
