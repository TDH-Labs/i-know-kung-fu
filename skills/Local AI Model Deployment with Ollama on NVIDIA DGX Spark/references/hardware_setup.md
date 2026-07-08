# NVIDIA DGX Spark Hardware Setup Guide

## Physical Connections
1. **Power Connection**: Connect the power cord to the first USB port adjacent to the power button
2. **Peripheral Setup**:
   - Use USB-C docking station for multi-monitor support (HDMI connections)
   - Connect keyboard/mouse via Bluetooth or wired USB
3. **Boot Process**:
   - Press the small power button (boot is silent with no audible indicators)
   - System runs Ubuntu-based OS with custom NVIDIA interface

## Hardware Specifications
- **Architecture**: NVIDIA Grace Blackwell (unified CPU/GPU chip)
- **Cores**: 20 ARM cores (10 Cortex + 10 additional Cortex)
- **Performance**: 1 petaflop (10^15) 4-bit floating point operations
- **Memory Bandwidth**: 273 GB/s
- **Storage**: 4TB SSD
- **GPU Specs**:
  - 6,144 CUDA cores
  - Supports models up to 200B parameters

## Monitoring
Access the DGX Dashboard to view:
- Real-time memory usage (128GB total)
- GPU utilization percentages
- System temperature and performance metrics

## Best Practices
1. Always verify peripheral connections before power-on
2. Monitor initial boot via connected displays (no audio cues)
3. Keep system firmware updated through Ubuntu package manager
4. Use the specification page as reference for model compatibility checks