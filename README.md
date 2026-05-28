# packettracer-kali-libfuse-fix
# Fix Cisco Packet Tracer 9.0 on Kali Linux (libfuse2 issue)

## Problem

When installing Cisco Packet Tracer on Kali Linux, you may see errors like:

```
dlopen(): error loading libfuse.so.2
AppImages require FUSE to run
```

or dependency errors related to `libfuse2`.

This happens because Kali Linux uses newer FUSE (libfuse3), and `libfuse2` is not included in the default repositories.

---

## Solution

We manually install `libfuse2` from Debian repositories.

---

### 1. Download libfuse2 package

```
wget http://ftp.debian.org/debian/pool/main/f/fuse/libfuse2_2.9.9-6+b1_amd64.deb
```

---

### 2. Install libfuse2

```
sudo dpkg -i libfuse2_2.9.9-6+b1_amd64.deb
```

---

### 3. Install Cisco Packet Tracer

```
sudo dpkg -i CiscoPacketTracer_900_Ubuntu_64bit.deb
```

During installation:
- Accept the EULA when prompted

---

### 4. Run Packet Tracer

```
packettracer
```

---

## Notes

- This issue happens because Packet Tracer requires `libfuse.so.2`
- Kali Linux uses `libfuse3` by default
- Installing `libfuse2` restores compatibility

---

## Result

Cisco Packet Tracer runs successfully on Kali Linux 🎉
