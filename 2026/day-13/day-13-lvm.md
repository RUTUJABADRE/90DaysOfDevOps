# What I learned

1. I learned how to create, manage, mount, and resize storage in Linux using LVM.

2. Storage has 3 layers (PV → VG → LV)
   - Disk becomes Physical Volume → combined into Volume Group → used to create Logical Volumes.

3. Volumes can be resized easily
   - I can increase storage using lvextend and then use resize2fs to make that space usable.

---

### How to create and use a filesystem

I learned that after creating a logical volume, it is not usable until:
- It is formatted using mkfs.ext4
- Then mounted to a directory

### Difference between storage size and filesystem size

I understood an important concept:
- lvextend increases the volume size
- resize2fs increases the filesystem size

### Real-world usefulness of LVM
- We can extend storage without downtime
- Easier management in servers and cloud environments

---
