# Chapter 1: Basic Device Configuration

## Concepts
- Switch Boot Sequence

---

## Switch Basic BOOT Sequence

When a Cisco device is powered on, it goes through these 5 steps:

### Step 1: Power-On Self-Test (POST)
- Switch loads a POST program stored in ROM (non-volatile, Read-Only Memory, stores essential program/firmware for device boot).

#### POST Tests:
1. **CPU**
  - Can execute instructions.
  - Read/write to memory.
  - Check for device faults/damages.

2. **DRAM** (Dynamic RAM, volatile memory, critical to switch operation)
  - Write and read back data to memory.

3. **Flash Device** (flash file system)
  - Checks the integrity of stored files and the presence of the IOS image.
