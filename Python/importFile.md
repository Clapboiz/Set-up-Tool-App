### Import file from different directory
**This is folder tree**

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/ebfc1972-d0ee-44f7-81b7-923c58350376)

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/f367f768-6b2c-4e45-89b4-4faee9cab7c4)

```
import os
import sys

sys.path.append(os.path.join(os.path.dirname(__file__), '..', 'Models'))
import dqn_model
dqn_model.dev_hello_world()
```
