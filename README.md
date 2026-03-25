<!-- BlackRoad SEO Enhanced -->

# hailo8 inference

> Part of **[BlackRoad OS](https://blackroad.io)** — Sovereign Computing for Everyone

[![BlackRoad OS](https://img.shields.io/badge/BlackRoad-OS-ff1d6c?style=for-the-badge)](https://blackroad.io)
[![BlackRoad AI](https://img.shields.io/badge/Org-BlackRoad-AI-2979ff?style=for-the-badge)](https://github.com/BlackRoad-AI)
[![License](https://img.shields.io/badge/License-Proprietary-f5a623?style=for-the-badge)](LICENSE)

**hailo8 inference** is part of the **BlackRoad OS** ecosystem — a sovereign, distributed operating system built on edge computing, local AI, and mesh networking by **BlackRoad OS, Inc.**

## About BlackRoad OS

BlackRoad OS is a sovereign computing platform that runs AI locally on your own hardware. No cloud dependencies. No API keys. No surveillance. Built by [BlackRoad OS, Inc.](https://github.com/BlackRoad-OS-Inc), a Delaware C-Corp founded in 2025.

### Key Features
- **Local AI** — Run LLMs on Raspberry Pi, Hailo-8, and commodity hardware
- **Mesh Networking** — WireGuard VPN, NATS pub/sub, peer-to-peer communication
- **Edge Computing** — 52 TOPS of AI acceleration across a Pi fleet
- **Self-Hosted Everything** — Git, DNS, storage, CI/CD, chat — all sovereign
- **Zero Cloud Dependencies** — Your data stays on your hardware

### The BlackRoad Ecosystem
| Organization | Focus |
|---|---|
| [BlackRoad OS](https://github.com/BlackRoad-OS) | Core platform and applications |
| [BlackRoad OS, Inc.](https://github.com/BlackRoad-OS-Inc) | Corporate and enterprise |
| [BlackRoad AI](https://github.com/BlackRoad-AI) | Artificial intelligence and ML |
| [BlackRoad Hardware](https://github.com/BlackRoad-Hardware) | Edge hardware and IoT |
| [BlackRoad Security](https://github.com/BlackRoad-Security) | Cybersecurity and auditing |
| [BlackRoad Quantum](https://github.com/BlackRoad-Quantum) | Quantum computing research |
| [BlackRoad Agents](https://github.com/BlackRoad-Agents) | Autonomous AI agents |
| [BlackRoad Network](https://github.com/BlackRoad-Network) | Mesh and distributed networking |
| [BlackRoad Education](https://github.com/BlackRoad-Education) | Learning and tutoring platforms |
| [BlackRoad Labs](https://github.com/BlackRoad-Labs) | Research and experiments |
| [BlackRoad Cloud](https://github.com/BlackRoad-Cloud) | Self-hosted cloud infrastructure |
| [BlackRoad Forge](https://github.com/BlackRoad-Forge) | Developer tools and utilities |

### Links
- **Website**: [blackroad.io](https://blackroad.io)
- **Documentation**: [docs.blackroad.io](https://docs.blackroad.io)
- **Chat**: [chat.blackroad.io](https://chat.blackroad.io)
- **Search**: [search.blackroad.io](https://search.blackroad.io)

---


**26 TOPS AI acceleration on Raspberry Pi 5**

## Hardware Setup

- **Device**: Raspberry Pi 5 (Cecilia)
- **Accelerator**: Hailo-8 M.2 Module
- **Performance**: 26 TOPS (15-30x more efficient than NVIDIA Jetson)

## Installation

```bash
# Install HailoRT
wget https://hailo.ai/downloads/hailort_4.17.0_arm64.deb
sudo dpkg -i hailort_4.17.0_arm64.deb

# Install Python bindings
pip install hailo-platform

# Verify installation
hailortcli scan
```

## Quick Start

```python
from hailo_platform import HailoDevice, HEF

# Load model
device = HailoDevice()
hef = HEF('models/yolov8n.hef')
network_group = device.configure(hef)

# Run inference
with network_group.activate():
    input_data = preprocess(image)
    output = network_group.run(input_data)
    results = postprocess(output)
```

## Compiled Models (.hef)

| Model | Use Case | Latency | TOPS Used |
|-------|----------|---------|-----------|
| YOLOv8n | Object Detection | 12ms | 8 |
| MobileNetV3 | Classification | 3ms | 4 |
| ResNet50 | Classification | 8ms | 12 |
| DeepLabV3 | Segmentation | 25ms | 18 |

## Model Compilation

```bash
# Install Hailo Model Zoo
pip install hailo-model-zoo

# Compile ONNX to HEF
hailo parser onnx model.onnx --hw-arch hailo8
hailo compiler model.har --hw-arch hailo8
```

## BlackRoad Integration

```bash
# On Cecilia Pi
curl -X POST http://cecilia:8080/infer \
  -F "image=@frame.jpg" \
  -F "model=yolov8n"
```

## Performance Metrics

- **Power Efficiency**: 2.5W typical
- **Throughput**: 3000+ FPS (INT8)
- **Memory**: 16GB shared with Pi 5

---

*BlackRoad OS - Edge AI Sovereignty on Cecilia*
