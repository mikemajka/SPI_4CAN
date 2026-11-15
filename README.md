# SPI_4CAN

## Overview

An FPGA-based SPI-to-CAN communication bridge implemented on a Lattice Mach XO2 FPGA. The FPGA acts as an SPI slave to a host MCU, receiving SPI messages and routing them to one of four independent CAN controllers implemented in the fabric. Each CAN controller exposes TX/RX signals for connection to an external CAN transceiver.

## Architecture

- **SPI Slave:** Receives commands from the host MCU.
- **Wishbone Controller:** Provides the internal communication interface.
- **CAN Dispatcher:** Decodes incoming messages and selects the destination CAN bus.
- **4× CAN Controllers:** Independent CAN controller instances implemented on the Lattice FPGA.
- **External Transceivers:** One CAN transceiver per channel for physical CAN bus connectivity.

## Motivation

This project explores an alternative to conventional SPI-to-CAN solutions such as the MCP2515, particularly for multi-bus robotics applications.

The University of Toronto RoboSoccer humanoid uses multiple CAN-connected actuators distributed across its limbs. Using 4x STM32 MCU, with each only controlling a CAN transceiver. The structure is simple and easy for prototyping; however, it is costly and introduces additional cost, routing complexity and board space.

By integrating multiple CAN controllers directly into an FPGA, this design aims to:

- Reduce MCU GPIO and SPI interface overhead.
- Consolidate multiple CAN controllers into a single FPGA.
- Support independent CAN buses for different actuator groups or robot limbs.
- Reduce external component count and PCB complexity.

The long-term goal is to explore integration into the University of Toronto RoboSoccer humanoid platform.

## Current Implementation

- SPI slave interface.
- Wishbone-based internal communication.
- Four CAN controller instances.
- SPI-to-CAN message routing.
- FPGA-level and board-level loopback testing.

## Future Work

- [ ] Module verification.
- [ ] Test simultaneous communication across four CAN buses.
- [ ] Evaluate integration with the RoboSoccer platform.

**Status:** Work in progress.
