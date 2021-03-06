# Wrapping-C--for-Python-InverseKinematics
Wrapping C++ Inverse Kinematics Functionalities for Python use

C Extension for Python of IKFast Module for baxter Robot

This repository wraps Forward-Kinematics and Inverse-Kinematics functions of custom-IKFast solver for Baxter robot. The .cpp functions are **computeIk** and **computeFk** respectively and can be found in the file named **baxter_left_arm_ikfast_solver.cpp** file. The python interface of these two functions are written in core **C** language and can be found in file named **myIKFastwrap.cpp**. The following shows the commands used to generate the shared object (.so) file named as **ikModule.so**.

```$ g++ -DNDEBUG -Wall -Wstrict-prototypes -fPIC -I/home/<user name>/anaconda3/include/python3.6m -c baxter_left_ik_solver_wrap.cpp -o ikModule.o -llapack```

```$ g++ -shared ikModule.o -o ikModule.so -llapack```

Once you are done with generating the **.so** file, copy and paste it to site-package folder of you python maintainer. For example if you are using **Anaconda** as your python package maintainer then, you should paste the **ikModule.so** file in the following path,
```$ ~/anaconda3/lib/python3.7/site-packages```

Next step is to call the wrapped functions from Python side using the provided python script named as **wrapper_application.py**. Look carefully the comments provided in the code for the input argument formats to call those functions.

**Note:** The input to IK or output of FK methods are not with respect to Baxter robot's base frame. One needs to generate suitable transform for IK input. Similarly one needs to multiply the output of FK with a fixed transform. We will talk about that fixed transform next.
