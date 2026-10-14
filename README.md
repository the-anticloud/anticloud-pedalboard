# PEDALBOARD

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-audio_consumer-lightgrey)

> Anticloud-hardened packaging of the upstream project `PEDALBOARD` in category **AUDIO CONSUMER**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** AUDIO CONSUMER · **Upstream:** https://github.com/spotify/pedalboard · **Upstream pin:** `f5e45049dfa8b33e8ee79a900b2b796a9dcae45f` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

![Pedalboard Logo](https://user-images.githubusercontent.com/213293/131147303-4805181a-c7d5-4afe-afb2-f591a4b8e586.png)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://github.com/spotify/pedalboard/blob/master/LICENSE)
[![Documentation](https://img.shields.io/badge/Documentation-on%20github.io-brightgreen)](https://spotify.github.io/pedalboard)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/pedalboard)](https://pypi.org/project/pedalboard)
[![Supported Platforms](https://img.shields.io/badge/platforms-macOS%20%7C%20Windows%20%7C%20Linux-green)](https://pypi.org/project/pedalboard)
[![Apple Silicon support for macOS and Linux (Docker)](https://img.shields.io/badge/Apple%20Silicon-macOS%20and%20Linux-brightgreen)](https://pypi.org/project/pedalboard)
[![PyPI - Wheel](https://img.shields.io/pypi/wheel/pedalboard)](https://pypi.org/project/pedalboard)
[![Test Badge](https://github.com/spotify/pedalboard/actions/workflows/all.yml/badge.svg)](https://github.com/spotify/pedalboard/actions/workflows/all.yml)
[![Coverage Badge](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/psobot/8736467e9952991ef44a67915ee7c762/raw/coverage.json)](https://gist.githubusercontent.com/psobot/8736467e9952991ef44a67915ee7c762/raw/coverage.json)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/pedalboard)](https://pypistats.org/packages/pedalboard)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7817838.svg)](https://doi.org/10.5281/zenodo.7817838)
[![GitHub project stars](https://img.shields.io/github/stars/spotify/pedalboard?style=social)](https://github.com/spotify/pedalboard/stargazers)

`pedalboard` is a Python library for working with audio: reading, writing, rendering, adding effects, and more. It supports most popular audio file formats and a number of common audio effects out of the box, and also allows the use of [VST3®](https://www.steinberg.net/en/company/technologies/vst3.html) and [Audio Unit](https://en.wikipedia.org/wiki/Audio_Units) formats for loading third-party software instruments and effects.

`pedalboard` was built by [Spotify's Audio Intelligence Lab](https://research.atspotify.com/audio-intelligence/) to enable using studio-quality audio effects from within Python and TensorFlow. Internally at Spotify, `pedalboard` is used for [data augmentation](https://en.wikipedia.org/wiki/Data_augmentation) to improve machine learning models and to help power features like [Spotify's AI DJ](https://newsroom.spotify.com/2023-02-22/spotify-debuts-a-new-ai-dj-right-in-your-pocket/) and [AI Voice Translation](https://newsroom.spotify.com/2023-09-25/ai-voice-translation-pilot-lex-fridman-dax-shepard-steven-bartlett/). `pedalboard` also helps in the process of content creation, making it possible to add effects to audio without using a Digital Audio Workstation.

[![Documentation](https://img.shields.io/badge/Documentation-on%20github.io-brightgreen)](https://spotify.github.io/pedalboard)

## Features 

 - Built-in audio I/O utilities ([pedalboard.io](https://spotify.github.io/pedalboard/reference/pedalboard.io.html))
   - Support for reading and writing AIFF, FLAC, MP3, OGG, and WAV files on all platforms with no dependencies
   - Additional support for reading AAC, AC3, WMA, and other formats depending on platform
   - Support for on-the-fly resampling of audio files and streams with `O(1)` memory usage
   - Live audio effects via <a href="https://spotify.github.io/pedalboard/reference/pedalboard.io.html#pedalboard.io.AudioStream"><code class="docutils literal"><span class="pre">AudioStream</span></code></a>
 - Built-in support for a number of basic audio transformations, including:
   - Guitar-style effects: `Chorus`, `Distortion`, `Phaser`, `Clipping`
   - Loudness and dynamic range effects: `Compressor`, `Gain`, `Limiter`
   - Equalizers and filters: `HighpassFilter`, `LadderFilter`, `LowpassFilter`
   - Spatial effects: `Convolution`, `Delay`, `Reverb`
   - Pitch effects: `PitchShift`
   - Lossy compression: `GSMFullRateCompressor`, `MP3Compressor`
   - Quality reduction: `Resample`, `Bitcrush`
 - Supports VST3® instrument and effect plugins on macOS, Windows, and Linux (<a href="https://spotify.github.io/pedalboard/reference/pedalboard.html#pedalboard.load_plugin"><code class="docutils literal"><span class="pre">pedalboard.load_plugin</span></code></a>)
 - Supports instrument and effect Audio Units on macOS
 - Strong thread-safety, memory usage, and speed guarantees
   - Releases Python's Global Interpreter Lock (GIL) to allow use of multiple CPU cores
     - No need to use `multiprocessing`!
   - Even when only using one thread:
     - Processes audio up to **300x** faster than [pySoX](https://github.com/rabitt/pysox) for single transforms, and 2-5x faster than [SoxBindings](https://github.com/pseeth/soxbindings) (via [iCorv](https://github.com/iCorv/pedalboard_with_tfdata))
     - Reads audio files up to **4x** faster than [librosa.load](https://librosa.org/doc/main/generated/librosa.load.html) (in many cases)
 - Tested compatibility with TensorFlow - can be used in `tf.data` pipelines!

## Installation

`pedalboard` is available via PyPI (via [Platform Wheels](https://packaging.python.org/guides/distributing-packages-using-setuptools/#platform-wheels)):
```
pip install pedalboard
```

If you are new to Python, follow [INSTALLATION.md](https://github.com/spotify/pedalboard/blob/master/INSTALLATION.md) for a robust guide.

### Compatibility

`pedalboard` is thoroughly tested with Python 3.10, 3.11, 3.12, 3.13, 3.14, and 3.15.

- Linux
  - Tested heavily in production use cases at Spotify
  - Tested automatically on GitHub with VSTs
  - Platform `manylinux` and `musllinux` wheels built for `x86_64` (Intel/AMD) and `aarch64` (ARM/Apple Silicon)
  - `x86_64` wheels require AVX support
  - Most Linux VSTs require a relatively modern Linux installation (with glibc > 2.27)
- macOS
  - Tested manually with VSTs and Audio Units

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml, requirements.txt; scanned in UPSTREAM_CLONE)
- Top-level source layout: `JUCE/`, `examples/`, `pedalboard/`, `pedalboard_native/`, `scripts/`, `tests/`, `vendors/`
- Snapshot size: **3766 files**, **362870 lines of code** (measured; see Benchmarks)
- Primary languages: `.c` (3010), `.h` (146), `.html` (125), `.in` (62), `.py` (56), `.am` (51)
- Upstream commit pinned for this packaging: `f5e45049dfa8b33e8ee79a900b2b796a9dcae45f`

---

## Installation

`pedalboard` is available via PyPI (via [Platform Wheels](https://packaging.python.org/guides/distributing-packages-using-setuptools/#platform-wheels)):
```
pip install pedalboard
```

If you are new to Python, follow [INSTALLATION.md](https://github.com/spotify/pedalboard/blob/master/INSTALLATION.md) for a robust guide.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

`pedalboard` was built by [Spotify's Audio Intelligence Lab](https://research.atspotify.com/audio-intelligence/) to enable using studio-quality audio effects from within Python and TensorFlow. Internally at Spotify, `pedalboard` is used for [data augmentation](https://en.wikipedia.org/wiki/Data_augmentation) to improve machine learning models and to help power features like [Spotify's AI DJ](https://newsroom.spotify.com/2023-02-22/spotify-debuts-a-new-ai-dj-right-in-your-pocket/) and [AI Voice Translation](https://newsroom.spotify.com/2023-09-25/ai-voice-translation-pilot-lex-fridman-dax-shepard-steven-bartlett/). `pedalboard` also helps in the process of content creation, making it possible to add effects to audio without using a Digital Audio Workstation.

[![Documentation](https://img.shields.io/badge/Documentation-on%20github.io-brightgreen)](https://spotify.github.io/pedalboard)

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/pedalboard)](https://pypi.org/project/pedalboard)
[![Supported Platforms](https://img.shields.io/badge/platforms-macOS%20%7C%20Windows%20%7C%20Linux-green)](https://pypi.org/project/pedalboard)
[![Apple Silicon support for macOS and Linux (Docker)](https://img.shields.io/badge/Apple%20Silicon-macOS%20and%20Linux-brightgreen)](https://pypi.org/project/pedalboard)
[![PyPI - Wheel](https://img.shields.io/pypi/wheel/pedalboard)](https://pypi.org/project/pedalboard)
[![Test Badge](https://github.com/spotify/pedalboard/actions/workflows/all.yml/badge.svg)](https://github.com/spotify/pedalboard/actions/workflows/all.yml)
[![Coverage Badge](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/psobot/8736467e9952991ef44a67915ee7c762/raw/coverage.json)](https://gist.githubusercontent.com/psobot/8736467e9952991ef44a67915ee7c762/raw/coverage.json)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/pedalboard)](https://pypistats.org/packages/pedalboard)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7817838.svg)](https://doi.org/10.5281/zenodo.7817838)
[![GitHub project stars](https://img.shields.io/github/stars/spotify/pedalboard?style=social)](https://github.com/spotify/pedalboard/stargazers)

`pedalboard` is a Python library for working with audio: reading, writing, rendering, adding effects, and more. It supports most popular audio file formats and a number of common audio effects out of the box, and also allows the use of [VST3®](https://www.steinberg.net/en/company/technologies/vst3.html) and [Audio Unit](https://en.wikipedia.org/wiki/Audio_Units) formats for loading third-party software instruments and effects.

`pedalboard` was built by [Spotify's Audio Intelligence Lab](https://research.atspotify.com/audio-intelligence/) to enable using studio-quality audio effects from within Python and TensorFlow. Internally at Spotify, `pedalboard` is used for [data augmentation](https://en.wikipedia.org/wiki/Data_augmentation) to improve machine learning models and to help power features like [Spotify's AI DJ](https://newsroom.spotify.com/2023-02-22/spotify-debuts-a-new-ai-dj-right-in-your-pocket/) and [AI Voice Translation](https://newsroom.spotify.com/2023-09-25/ai-voice-translation-pilot-lex-fridman-dax-shepard-steven-bartlett/). `pedalboard` also helps in the process of content creation, making it possible to add effects to audio without using a Digital Audio Workstation.

[![Documentation](https://img.shields.io/badge/Documentation-on%20github.io-brightgreen)](https://spotify.github.io/pedalboard)

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml, requirements.txt |
| Files in snapshot | 3766 |
| Lines of code | 362870 |
| Dependency references | 74 |
| Dependencies by ecosystem | native: 9, pypi: 65 |
| Upstream license | GPL-3.0 |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| native | Python | - | CMakeLists.txt |
| native | pybind11 | - | CMakeLists.txt |
| native | Python | - | CMakeLists.txt |
| native | Python | - | CMakeLists.txt |
| native | PkgConfig | - | CMakeLists.txt |
| native | FREETYPE | - | CMakeLists.txt |
| native | ALSA | - | CMakeLists.txt |
| pypi | numpy | - | pyproject.toml |
| pypi | -DJUCE_DISPLAY_SPLASH_SCREEN | =1 | setup.py |
| pypi | -DJUCE_USE_DARK_SPLASH_SCREEN | =1 | setup.py |
| pypi | -DJUCE_MODULE_AVAILABLE_juce_audio_basics | =1 | setup.py |
| pypi | -DJUCE_MODULE_AVAILABLE_juce_audio_formats | =1 | setup.py |
| pypi | -DJUCE_MODULE_AVAILABLE_juce_audio_processors | =1 | setup.py |
| pypi | -DJUCE_MODULE_AVAILABLE_juce_core | =1 | setup.py |
| pypi | -DJUCE_MODULE_AVAILABLE_juce_data_structures | =1 | setup.py |
| ... | (59 more) | | |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

No configuration section was found in the upstream readme. Configuration-relevant files detected in this project directory:

- `CMakeLists.txt`
- `pyproject.toml`
- `tox.ini`

Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# How to Contribute

We'd love to get patches from you!

## Getting Started

### Prerequisites

To compile Pedalboard from scratch, the following packages will need to be installed:

- [Python 3.8](https://www.python.org/downloads/) or higher.
- A C++ compiler, e.g. `gcc`, `clang`, etc.
  - On macOS, a working Xcode installation should provide this.
- On Linux:
  - FreeType 2 (`libfreetype-dev`, `libfreetype2-dev`, or `freetype2-devel`)
  - X11 (`xorg-dev` should do)

### Building Pedalboard

```shell
git source --recurse-submodules --shallow-submodules git@github.com:spotify/pedalboard.git
cd pedalboard
pip3 install pybind11 tox
pip3 install .
```

To compile a debug build of `pedalboard` that allows using a debugger (like gdb or lldb), use the following command to build the package locally and install a symbolic link for debugging:
```shell
python3 setup.py build develop
```

Then, you can `import pedalboard` from Python (or run the tests with `tox`) to test out your local changes.

Linux x86_64 builds target the portable AVX baseline by default. To optimize a local
build for the current machine instead, set `USE_MARCH_NATIVE=1` while building.
The previous `USE_PORTABLE_SIMD` variable is no longer used; builds that set it remain
portable because AVX is now the default.

> If you're on macOS or Linux, you can try to compile a debug build _faster_ by using [Ccache](https://ccache.dev/):
> ## macOS
> ```shell
> brew install ccache
> rm -rf build && CC="ccache clang" CXX="ccache clang++" DEBUG=1 python3 -j8 -m pip install -e .
> ```
> ## Linux
> e.g.
> ```shell
> sudo yum install ccache  # or apt, if on a Debian
> 
> # If using GCC:
> rm -rf build && CC="ccache gcc" CXX="scripts/ccache_g++" DEBUG=1 python3 setup.py build -j8 develop
> 
> # ...or if using Clang:
> rm -rf build && CC="ccache clang" CXX="scripts/ccache_clang++" DEBUG=1 python3 setup.py build -j8 develop
> ```

By default, [all `.cpp` and `.mm` files in the `pedalboard` directory (or subdirectories)](https://github.com/spotify/pedalboard/blob/master/setup.py#L129) will be automatically compiled by `setup.py`.

While `pedalboard` is mostly C++ code, it ships with `.pyi` files to allow for type hints in text editors and via MyPy. To update the type hint files, use the following commands:

```shell
# Use pybind11-stubgen to create intermediate stub files:
pybind11-stubgen -o stubs_output pedalboard pedalboard_native --no-setup-py
# Post-process the stub files into more human-readable, usable ones:

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: GPL-3.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
                    GNU GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007

 Copyright (C) 2007 Free Software Foundation, Inc. <https://fsf.org/>
 Everyone is permitted to copy and distribute verbatim copies
 of this license document, but changing it is not allowed.

                            Preamble

  The GNU General Public License is a free, copyleft license for
software and other kinds of works.

  The licenses for most software and other practical works are designed
to take away your freedom to share and change the works.  By contrast,
the GNU General Public License is intended to guarantee your freedom to
share and change all versions of a program--to make sure it remains free
software for all its users.  We, the Free Software Foundation, use the
GNU General Public License for most of our software; it applies also to
any other work released this way by its authors.  You can apply it to
your programs, too.
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original GPL-3.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `GPL-3.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `PEDALBOARD` (category: AUDIO CONSUMER)
- **Upstream URL:** https://github.com/spotify/pedalboard
- **Pinned commit (SHA):** `f5e45049dfa8b33e8ee79a900b2b796a9dcae45f`
- **Branch:** master
- **Pin provenance:** resolved during the second documentation pass. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`b05332ff3e937ede11ec190f3be16473a9b28019c3db50689f2ece3f7d901abc`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

