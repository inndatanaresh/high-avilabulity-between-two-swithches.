# High Availability Between Two Switches

## Requirements for Configuration

- Two Layer 2 (L2) or Layer 3 (L3) switches connected in parallel.
- VLAN must be configured on both switches before proceeding with high availability setup.

## High Availability Configuration Steps

### Step 1: VLAN Configuration
Before setting up high availability, ensure that VLANs are properly configured on both switches.

```bash
configure terminal
vlan 10
exit
```

### Step 2: VRRP (Virtual Router Redundancy Protocol) Configuration

1. Enable the switch:
```bash
enable
```

2. Enter configuration mode:
```bash
configure terminal
```

3. Interface with the VLAN:
```bash
interface vlan 1
```

4. Configure VRRP:
```bash
vrrp <group-id> ip <virtual-ip>
```
**Note:** The virtual IP and VLAN IP should not be the same.

5. Assign priority to VRRP:
```bash
vrrp <group-id> priority <value>
```
Higher priority determines the active switch.

6. Repeat the above steps on both switches.

### Step 3: Verification
After configuration, verify the setup using:
```bash
show vrrp
show vrrp brief
```
Run these commands on both switches to ensure proper failover setup.

### Step 4: Standby Configuration
Repeat the VRRP configuration commands on the second switch to act as a standby router.

---
This configuration should work in real-time environments, even if it does not function in Packet Tracer. Ensure that both switches have proper connectivity and VLANs are set correctly.
