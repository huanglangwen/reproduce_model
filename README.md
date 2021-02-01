# PyBox
1. Build a docker image for PyBox using `docker build . -t pybox` under the `pybox` subfolder.
2. Run and enter the docker container using the built image `docker run -it --rm pybox`.
3. Inside the container, enter the directory `/Code/Git_repos/PyBox/Aerosol/f2py`.
4. Execute `python Aerosol_simulation_f2py.py` to run the mixed-phase simulation for Alpha-Pinene mechanism.
5. Enter the directory `/Code/Git_repos/PyBox/f2py`, and execute `python Gas_simulation_f2py.py` to run the gas phase only simulation for Alpha-Pinene mechanism.

# JlBox
1. Build a docker image for JlBox using `docker build . -t jlbox` under the `jlbox` subfolder.
2. Run and enter the docker container using the built image `docker run -it --rm jlbox`.
3. Insider the container, where the julia console is activated automatically, run `using Pkg;Pkg.activate(".");Pkg.instantiate()` to retrieve environment for reproduce.
4. Run `include("example/Simulation_aerosol.jl")` to run the mixed-phase simuation for Alpha-Pinene mechanism.
5. Run `include("Simulation_gas.jl")` to run the gas phase only simulation for Alpha-Pinene mechanism.

# KPP
1. Build a docker image for KPP generated model using `docker build . -t kpp` under the `kpp` subfolder.
2. Run gas phase only simulation for Alpha-Pinene mechanism using `docker run --rm kpp`
