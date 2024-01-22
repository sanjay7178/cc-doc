---
title: Archive Specification
description: >
  Specifications used in on-disk JSON job archive
---

## Cluster Definition Specifications

```json
{
    "$schema": "http://json-schema.org/draft/2020-12/schema",
    "$id": "cluster.schema.json",
    "title": "HPC cluster description",
    "description": "Meta data information of a HPC cluster",
    "type": "object",
    "properties": {
        "name": {
            "description": "The unique identifier of a cluster",
            "type": "string"
        },
        "metricConfig": {
            "description": "Metric specifications",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "name": {
                        "description": "Metric name",
                        "type": "string"
                    },
                    "unit": {
                        "description": "Metric unit",
                        "$ref": "embedfs://unit.schema.json"
                    },
                    "scope": {
                        "description": "Native measurement resolution",
                        "type": "string"
                    },
                    "timestep": {
                        "description": "Frequency of timeseries points",
                        "type": "integer"
                    },
                    "aggregation": {
                        "description": "How the metric is aggregated",
                        "type": "string",
                        "enum": [
                            "sum",
                            "avg"
                        ]
                    },
                    "peak": {
                        "description": "Metric peak threshold (Upper metric limit)",
                        "type": "number"
                    },
                    "normal": {
                        "description": "Metric normal threshold",
                        "type": "number"
                    },
                    "caution": {
                        "description": "Metric caution threshold (Suspicious but does not require immediate action)",
                        "type": "number"
                    },
                    "alert": {
                        "description": "Metric alert threshold (Requires immediate action)",
                        "type": "number"
                    },
                    "subClusters": {
                        "description": "Array of cluster hardware partition metric thresholds",
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "name": {
                                    "description": "Hardware partition name",
                                    "type": "string"
                                },
                                "peak": {
                                    "type": "number"
                                },
                                "normal": {
                                    "type": "number"
                                },
                                "caution": {
                                    "type": "number"
                                },
                                "alert": {
                                    "type": "number"
                                },
                                "remove": {
                                    "type": "boolean"
                                }
                            },
                            "required": [
                                "name"
                            ]
                        }
                    }
                },
                "required": [
                    "name",
                    "unit",
                    "scope",
                    "timestep",
                    "aggregation",
                    "peak",
                    "normal",
                    "caution",
                    "alert"
                ]
            },
            "minItems": 1
        },
        "subClusters": {
            "description": "Array of cluster hardware partitions",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "name": {
                        "description": "Hardware partition name",
                        "type": "string"
                    },
                    "processorType": {
                        "description": "Processor type",
                        "type": "string"
                    },
                    "socketsPerNode": {
                        "description": "Number of sockets per node",
                        "type": "integer"
                    },
                    "coresPerSocket": {
                        "description": "Number of cores per socket",
                        "type": "integer"
                    },
                    "threadsPerCore": {
                        "description": "Number of SMT threads per core",
                        "type": "integer"
                    },
                    "flopRateScalar": {
                        "description": "Theoretical node peak flop rate for scalar code in GFlops/s",
                        "type": "object",
                        "properties": {
                            "unit": {
                                "description": "Metric unit",
                                "$ref": "embedfs://unit.schema.json"
                            },
                            "value": {
                                "type": "number"
                            }
                        }
                    },
                    "flopRateSimd": {
                        "description": "Theoretical node peak flop rate for SIMD code in GFlops/s",
                        "type": "object",
                        "properties": {
                            "unit": {
                                "description": "Metric unit",
                                "$ref": "embedfs://unit.schema.json"
                            },
                            "value": {
                                "type": "number"
                            }
                        }
                    },
                    "memoryBandwidth": {
                        "description": "Theoretical node peak memory bandwidth in GB/s",
                        "type": "object",
                        "properties": {
                            "unit": {
                                "description": "Metric unit",
                                "$ref": "embedfs://unit.schema.json"
                            },
                            "value": {
                                "type": "number"
                            }
                        }
                    },
                    "nodes": {
                        "description": "Node list expression",
                        "type": "string"
                    },
                    "topology": {
                        "description": "Node topology",
                        "type": "object",
                        "properties": {
                            "node": {
                                "description": "HwTread lists of node",
                                "type": "array",
                                "items": {
                                    "type": "integer"
                                }
                            },
                            "socket": {
                                "description": "HwTread lists of sockets",
                                "type": "array",
                                "items": {
                                    "type": "array",
                                    "items": {
                                        "type": "integer"
                                    }
                                }
                            },
                            "memoryDomain": {
                                "description": "HwTread lists of memory domains",
                                "type": "array",
                                "items": {
                                    "type": "array",
                                    "items": {
                                        "type": "integer"
                                    }
                                }
                            },
                            "die": {
                                "description": "HwTread lists of dies",
                                "type": "array",
                                "items": {
                                    "type": "array",
                                    "items": {
                                        "type": "integer"
                                    }
                                }
                            },
                            "core": {
                                "description": "HwTread lists of cores",
                                "type": "array",
                                "items": {
                                    "type": "array",
                                    "items": {
                                        "type": "integer"
                                    }
                                }
                            },
                            "accelerators": {
                                "type": "array",
                                "description": "List of of accelerator devices",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "id": {
                                            "type": "string",
                                            "description": "The unique device id"
                                        },
                                        "type": {
                                            "type": "string",
                                            "description": "The accelerator type",
                                            "enum": [
                                                "Nvidia GPU",
                                                "AMD GPU",
                                                "Intel GPU"
                                            ]
                                        },
                                        "model": {
                                            "type": "string",
                                            "description": "The accelerator model"
                                        }
                                    },
                                    "required": [
                                        "id",
                                        "type",
                                        "model"
                                    ]
                                }
                            }
                        },
                        "required": [
                            "node",
                            "socket",
                            "memoryDomain"
                        ]
                    }
                },
                "required": [
                    "name",
                    "nodes",
                    "topology",
                    "processorType",
                    "socketsPerNode",
                    "coresPerSocket",
                    "threadsPerCore",
                    "flopRateScalar",
                    "flopRateSimd",
                    "memoryBandwidth"
                ]
            },
            "minItems": 1
        }
    },
    "required": [
        "name",
        "metricConfig",
        "subClusters"
    ]
}
```

## Job Meta-Data Specifications

```json
{
    "$schema": "http://json-schema.org/draft/2020-12/schema",
    "$id": "embedfs://job-meta.schema.json",
    "title": "Job meta data",
    "description": "Meta data information of a HPC job",
    "type": "object",
    "properties": {
        "jobId": {
            "description": "The unique identifier of a job",
            "type": "integer"
        },
        "user": {
            "description": "The unique identifier of a user",
            "type": "string"
        },
        "project": {
            "description": "The unique identifier of a project",
            "type": "string"
        },
        "cluster": {
            "description": "The unique identifier of a cluster",
            "type": "string"
        },
        "subCluster": {
            "description": "The unique identifier of a sub cluster",
            "type": "string"
        },
        "partition": {
            "description": "The Slurm partition to which the job was submitted",
            "type": "string"
        },
        "arrayJobId": {
            "description": "The unique identifier of an array job",
            "type": "integer"
        },
        "numNodes": {
            "description": "Number of nodes used",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "numHwthreads": {
            "description": "Number of HWThreads used",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "numAcc": {
            "description": "Number of accelerators used",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "exclusive": {
            "description": "Specifies how nodes are shared. 0 - Shared among multiple jobs of multiple users, 1 - Job exclusive, 2 - Shared among multiple jobs of same user",
            "type": "integer",
            "minimum": 0,
            "maximum": 2
        },
        "monitoringStatus": {
            "description": "State of monitoring system during job run",
            "type": "integer"
        },
        "smt": {
            "description": "SMT threads used by job",
            "type": "integer"
        },
        "walltime": {
            "description": "Requested walltime of job in seconds",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "jobState": {
            "description": "Final state of job",
            "type": "string",
            "enum": [
                "completed",
                "failed",
                "cancelled",
                "stopped",
                "out_of_memory",
                "timeout"
            ]
        },
        "startTime": {
            "description": "Start epoch time stamp in seconds",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "duration": {
            "description": "Duration of job in seconds",
            "type": "integer",
            "exclusiveMinimum": 0
        },
        "resources": {
            "description": "Resources used by job",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "hostname": {
                        "type": "string"
                    },
                    "hwthreads": {
                        "type": "array",
                        "description": "List of OS processor ids",
                        "items": {
                            "type": "integer"
                        }
                    },
                    "accelerators": {
                        "type": "array",
                        "description": "List of of accelerator device ids",
                        "items": {
                            "type": "string"
                        }
                    },
                    "configuration": {
                        "type": "string",
                        "description": "The configuration options of the node"
                    }
                },
                "required": [
                    "hostname"
                ],
                "minItems": 1
            }
        },
        "metaData": {
            "description": "Additional information about the job",
            "type": "object",
            "properties": {
                "jobScript": {
                    "type": "string",
                    "description": "The batch script of the job"
                },
                "jobName": {
                    "type": "string",
                    "description": "Slurm Job name"
                },
                "slurmInfo": {
                    "type": "string",
                    "description": "Additional slurm infos as show by scontrol show job"
                }
            }
        },
        "tags": {
            "description": "List of tags",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "name": {
                        "type": "string"
                    },
                    "type": {
                        "type": "string"
                    }
                },
                "required": [
                    "name",
                    "type"
                ]
            },
            "uniqueItems": true
        },
        "statistics": {
            "description": "Job statistic data",
            "type": "object",
            "properties": {
                "mem_used": {
                    "description": "Memory capacity used (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "cpu_load": {
                    "description": "CPU requested core utilization (load 1m) (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "flops_any": {
                    "description": "Total flop rate with DP flops scaled up (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "mem_bw": {
                    "description": "Main memory bandwidth (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "net_bw": {
                    "description": "Total fast interconnect network bandwidth (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "file_bw": {
                    "description": "Total file IO bandwidth (required)",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "ipc": {
                    "description": "Instructions executed per cycle",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "cpu_user": {
                    "description": "CPU user active core utilization",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "flops_dp": {
                    "description": "Double precision flop rate",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "flops_sp": {
                    "description": "Single precision flops rate",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "rapl_power": {
                    "description": "CPU power consumption",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "acc_used": {
                    "description": "GPU utilization",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "acc_mem_used": {
                    "description": "GPU memory capacity used",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "acc_power": {
                    "description": "GPU power consumption",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "clock": {
                    "description": "Average core frequency",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "eth_read_bw": {
                    "description": "Ethernet read bandwidth",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "eth_write_bw": {
                    "description": "Ethernet write bandwidth",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "ic_rcv_packets": {
                    "description": "Network interconnect read packets",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "ic_send_packets": {
                    "description": "Network interconnect send packet",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "ic_read_bw": {
                    "description": "Network interconnect read bandwidth",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "ic_write_bw": {
                    "description": "Network interconnect write bandwidth",
                    "$ref": "embedfs://job-metric-statistics.schema.json"
                },
                "filesystems": {
                    "description": "Array of filesystems",
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "name": {
                                "type": "string"
                            },
                            "type": {
                                "type": "string",
                                "enum": [
                                    "nfs",
                                    "lustre",
                                    "gpfs",
                                    "nvme",
                                    "ssd",
                                    "hdd",
                                    "beegfs"
                                ]
                            },
                            "read_bw": {
                                "description": "File system read bandwidth",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "write_bw": {
                                "description": "File system write bandwidth",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "read_req": {
                                "description": "File system read requests",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "write_req": {
                                "description": "File system write requests",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "inodes": {
                                "description": "File system write requests",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "accesses": {
                                "description": "File system open and close",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "fsync": {
                                "description": "File system fsync",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "create": {
                                "description": "File system create",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "open": {
                                "description": "File system open",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "close": {
                                "description": "File system close",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            },
                            "seek": {
                                "description": "File system seek",
                                "$ref": "embedfs://job-metric-statistics.schema.json"
                            }
                        },
                        "required": [
                            "name",
                            "type",
                            "read_bw",
                            "write_bw"
                        ]
                    },
                    "minItems": 1
                }
            },
            "required": [
                "cpu_user",
                "cpu_load",
                "mem_used",
                "flops_any",
                "mem_bw"
            ]
        }
    },
    "required": [
        "jobId",
        "user",
        "project",
        "cluster",
        "subCluster",
        "numNodes",
        "exclusive",
        "startTime",
        "jobState",
        "duration",
        "resources",
        "statistics"
    ]
}
```

## Job Metric-Data Specifications

```json
{
    "$schema": "http://json-schema.org/draft/2020-12/schema",
    "$id": "embedfs://job-data.schema.json",
    "title": "Job metric data list",
    "description": "Collection of metric data of a HPC job",
    "type": "object",
    "properties": {
        "mem_used": {
            "description": "Memory capacity used",
            "type": "object",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "node"
            ]
        },
        "flops_any": {
            "description": "Total flop rate with DP flops scaled up",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "mem_bw": {
            "description": "Main memory bandwidth",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "net_bw": {
            "description": "Total fast interconnect network bandwidth",
            "type": "object",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "node"
            ]
        },
        "ipc": {
            "description": "Instructions executed per cycle",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "cpu_user": {
            "description": "CPU user active core utilization",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "cpu_load": {
            "description": "CPU requested core utilization (load 1m)",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "node"
            ]
        },
        "flops_dp": {
            "description": "Double precision flop rate",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "flops_sp": {
            "description": "Single precision flops rate",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "vectorization_ratio": {
            "description": "Fraction of arithmetic instructions using SIMD instructions",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "cpu_power": {
            "description": "CPU power consumption",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "mem_power": {
            "description": "Memory power consumption",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "acc_utilization": {
            "description": "GPU utilization",
            "properties": {
                "accelerator": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "accelerator"
            ]
        },
        "acc_mem_used": {
            "description": "GPU memory capacity used",
            "properties": {
                "accelerator": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "accelerator"
            ]
        },
        "acc_power": {
            "description": "GPU power consumption",
            "properties": {
                "accelerator": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "accelerator"
            ]
        },
        "clock": {
            "description": "Average core frequency",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "socket": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "memoryDomain": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "core": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                },
                "hwthread": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "minProperties": 1
        },
        "eth_read_bw": {
            "description": "Ethernet read bandwidth",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "node"
            ]
        },
        "eth_write_bw": {
            "description": "Ethernet write bandwidth",
            "properties": {
                "node": {
                    "$ref": "embedfs://job-metric-data.schema.json"
                }
            },
            "required": [
                "node"
            ]
        },
        "filesystems": {
            "description": "Array of filesystems",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "name": {
                        "type": "string"
                    },
                    "type": {
                        "type": "string",
                        "enum": [
                            "nfs",
                            "lustre",
                            "gpfs",
                            "nvme",
                            "ssd",
                            "hdd",
                            "beegfs"
                        ]
                    },
                    "read_bw": {
                        "description": "File system read bandwidth",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "write_bw": {
                        "description": "File system write bandwidth",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "read_req": {
                        "description": "File system read requests",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "write_req": {
                        "description": "File system write requests",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "inodes": {
                        "description": "File system write requests",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "accesses": {
                        "description": "File system open and close",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "fsync": {
                        "description": "File system fsync",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "create": {
                        "description": "File system create",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "open": {
                        "description": "File system open",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "close": {
                        "description": "File system close",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    },
                    "seek": {
                        "description": "File system seek",
                        "properties": {
                            "node": {
                                "$ref": "embedfs://job-metric-data.schema.json"
                            }
                        },
                        "required": [
                            "node"
                        ]
                    }
                },
                "required": [
                    "name",
                    "type",
                    "read_bw",
                    "write_bw"
                ]
            },
            "minItems": 1
        }
    },
    "ic_rcv_packets": {
        "description": "Network interconnect read packets",
        "properties": {
            "node": {
                "$ref": "embedfs://job-metric-data.schema.json"
            }
        },
        "required": [
            "node"
        ]
    },
    "ic_send_packets": {
        "description": "Network interconnect send packet",
        "properties": {
            "node": {
                "$ref": "embedfs://job-metric-data.schema.json"
            }
        },
        "required": [
            "node"
        ]
    },
    "ic_read_bw": {
        "description": "Network interconnect read bandwidth",
        "properties": {
            "node": {
                "$ref": "embedfs://job-metric-data.schema.json"
            }
        },
        "required": [
            "node"
        ]
    },
    "ic_write_bw": {
        "description": "Network interconnect write bandwidth",
        "properties": {
            "node": {
                "$ref": "embedfs://job-metric-data.schema.json"
            }
        },
        "required": [
            "node"
        ]
    },
    "required": [
        "cpu_user",
        "cpu_load",
        "mem_used",
        "flops_any",
        "mem_bw",
        "net_bw",
        "filesystems"
    ]
}
```
