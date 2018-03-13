# CK repository for Quantum Information Software Kit (QISKit)

## Installation 

### Install global prerequisites (Ubuntu, Debian)

```
$ sudo apt install build-essential
$ sudo apt install libblas-dev liblapack-dev
```

### Install Python 3

**NB:** Python 2 is **not** supported.

```
$ sudo apt install python3 python3-pip
```

### Install Collective Knowledge

```
$ sudo pip3 install ck
```


### Install this CK repository with all its dependencies (other CK repos to reuse artifacts)

```
$ ck pull repo:ck-qiskit
```

## Install Quantum Information Software Kit (QISKit)

```
$ ck list ck-qiskit:package:*
$ ck install package:lib-qiskit
```

## IBM Quantum Experience

### Documentation
- [Main Repo](https://github.com/QISKit)
- [IBM Quantum Experience user guides](https://github.com/QISKit/ibmqx-user-guides)

- QISKit [SDK](https://github.com/QISKit/qiskit-sdk-py/blob/master/README.md)
- QISKit [Getting Started Guide](https://www.qiskit.org/documentation/quickstart.html)
- QISKit [Tutorial](https://github.com/QISKit/qiskit-tutorial)


At a lower level, you can use the native [QISKit Python API](https://github.com/QISKit/qiskit-api-py) to call [OpenQASM](https://github.com/QISKit/openqasm/blob/master/README.md).

### Real Backends

- [IBMQX2](https://github.com/QISKit/ibmqx-backend-information/blob/master/backends/ibmqx2/README.md) 
- [IBMQX3](https://github.com/QISKit/ibmqx-backend-information/blob/master/backends/ibmqx3/README.md)
- [IBMQX4](https://github.com/QISKit/ibmqx-backend-information/blob/master/backends/ibmqx4/README.md)
- [IBMQX5](https://github.com/QISKit/ibmqx-backend-information/blob/master/backends/ibmqx5/README.md)

### Local Simulators

- `local_clifford_simulator`
- `local_qasm_simulator`
- `local_unitary_simulator`
- `local_projectq_simulator`
- `local_qiskit_simulator`


## Run Programs

Get a valid [IBM_API_TOKEN](https://quantumexperience.ng.bluemix.net/qx/login) `->` myaccount `->` advanced

**NB:** An exception might be raised due to login failure (missing or invalid token).

#### Run an example using a local simulator

```
$ ck run program:qiskit-demo --cmd_key=hello \
  --env.CK_IBM_BACKEND=local_qasm_simulator
```


#### Run an example using a remote simulator

```
$ ck run program:qiskit-demo --cmd_key=hello \
  --env.CK_IBM_BACKEND=ibmqx_qasm_simulator --env.CK_IBM_API_TOKEN=<YOUR_TOKEN>
```

#### Run an example using IBMQX5 

```
$ ck run program:qiskit-demo --cmd_key=hello \
  --env.CK_IBM_BACKEND=ibmqx5 --env.CK_IBM_API_TOKEN=<YOUR_TOKEN>
```


## FAQ

### How to register my libraries and tools with CK?

CK will try to detect compilers and libraries automatically, but you can also
register them as follows:

```
$ ck detect soft:compiler.gcc
$ ck detect soft:lib.blas
$ ck detect soft:lib.lapack
```

### Where does CK store my program and its output?

A program can be located on disk by its name as follows:
```
$ ck find program:projectq-shor
/home/flavio/CK-REPOS/ck-qiskit/program/qiskit-shor
$ ls `ck find program:qiskit-shor`
quantum_random_numbers.py  shor.py
```

Temporary files (including the executable, `stderr` and `stdout`) are in the `tmp` directory:
```
$ cd `ck find program:qiskit-shor`/tmp
```

## Troubleshooting

**TODO**