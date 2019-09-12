# PyCM730
Python Package for Robotis CM730 Robot Controller

**Install dependencies**
```bash
git clone https://github.com/ROBOTIS-GIT/DynamixelSDK.git
cd DynamixelSDK/python
python setup.py install
```
**Disable root access for serial port**
```bash
sudo apt remove modemmanager
sudo usermod -a -G dialout username
```
**Example code**
```python
def main():
    cm730 = CM730()
    cm730.connect()
    cm730.dxl_on()
    time.sleep(1)
    cm730.check_ID(0, 255)
    cm730.servo_sync_enable_torque([18, 21])
    for i in range(0, 1000, 10):
        cm730.servo_sync_write_position([18, 21], [i, i])
        print(cm730.servo_sync_read_position([18, 21]))
        time.sleep(0.5)
    cm730.servo_sync_disable_torque([18, 21])
    cm730.disconnect()
    
if __name__ == "__main__":
    main()
```
