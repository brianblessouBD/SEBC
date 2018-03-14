`curl http://admin:admin@52.138.182.88:7180/api/v2/cm/deployment`
```
{
  "timestamp" : "2018-03-14T09:20:43.445Z",
  "clusters" : [ {
    "name" : "Cluster 1",
    "version" : "CDH5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-2e17d58342866b9e149334acd94ae47b",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "77736adb-bc63-4161-9ba0-d852b2658b00"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5038mc2x3cg1xn4wlbetc5vjl"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4fk2tgll132bbbb5o3pkrpzvq"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-e46b06adbdb40a0b9acb3a40fb322ac1",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "71gymtrn36ucu1dpxpgayz3zk"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "lion.cdh-bootcamp-bb"
          }, {
            "name" : "oozie_database_password",
            "value" : "password"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozieuser"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-73b6bc98e00d6de1a972ba263c51ff2a",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6bxs3klvrsfjo510rw412m5pl"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "lion.cdh-bootcamp-bb"
        }, {
          "name" : "database_password",
          "value" : "password"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "database_user",
          "value" : "hueuser"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-2f8b6f6c84aaccc0ff33d22dff447e76"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-73b6bc98e00d6de1a972ba263c51ff2a",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7gym1bvg4msjbu3pqu9j33kgb"
          }, {
            "name" : "secret_key",
            "value" : "v8nV2JAb7DhOiRhRqKOg0leVH5hzpS"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/mnt/resource/dfs/dn"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/mnt/resource/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/mnt/resource/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "C8XIUveeWlA1vo6wZ5Iq139lhTaTnP"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "V3G8ApO4YM169H4cELUQtOnwgJBDYZ"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "TNIc9lsYF3TiIZnlrcxgqQHRg10Sbu"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-e46b06adbdb40a0b9acb3a40fb322ac1",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-2e17d58342866b9e149334acd94ae47b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "77736adb-bc63-4161-9ba0-d852b2658b00"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5taw1ce96tjci6jkvi18sbh4f"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1s7i16h70p2sp298j6jv9ju0j"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-73b6bc98e00d6de1a972ba263c51ff2a",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "brtw0piubts3ydik69z4oz3x1"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-e46b06adbdb40a0b9acb3a40fb322ac1",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4a9y0fay8eamljn7dlnx5ee5h"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "namenode_id",
            "value" : "44"
          }, {
            "name" : "role_jceks_password",
            "value" : "x1rbusyr3y53uc1ydoqobjx"
          } ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-2e17d58342866b9e149334acd94ae47b",
        "type" : "SECONDARYNAMENODE",
        "hostRef" : {
          "hostId" : "77736adb-bc63-4161-9ba0-d852b2658b00"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4eu62vmd6sd4kakz42yr2kt3i"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/mnt/resource/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/mnt/resource/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3701"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "12825"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "4"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "UhGRa3lIBfTlnkv15aeobSFeOOQlqc"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-73b6bc98e00d6de1a972ba263c51ff2a",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dp3o8ygbedz17lzqn5ievzxmo"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-2e17d58342866b9e149334acd94ae47b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "77736adb-bc63-4161-9ba0-d852b2658b00"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "emm23klc87hyte1kgq05071x4"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "824mlwh03ueauuqh7db34oicu"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-73b6bc98e00d6de1a972ba263c51ff2a",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8aezu0u5yh7okyfiljdtrujan"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-e46b06adbdb40a0b9acb3a40fb322ac1",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "nnx9j1gkf1nx5guxq81uc216"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-e46b06adbdb40a0b9acb3a40fb322ac1",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "51"
          }, {
            "name" : "role_jceks_password",
            "value" : "e1pw0ao7z3bs149bnb7ats61"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "2985295872"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "298529587"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "2985295872"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3298662809"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "555"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "lion.cdh-bootcamp-bb"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "password"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "hiveuser"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "76eibojlyz7tboa8ow1yluypd"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-2f8b6f6c84aaccc0ff33d22dff447e76",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "aopp0975b9dextra671i3h2e0"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "cbbe5370-6204-42a9-bcc1-871893c22bac",
    "ipAddress" : "10.3.12.5",
    "hostname" : "elephant.cdh-bootcamp-bb",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "8218abd9-f150-49a1-884e-8a962a2073aa",
    "ipAddress" : "10.3.12.8",
    "hostname" : "horse.cdh-bootcamp-bb",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57",
    "ipAddress" : "10.3.12.4",
    "hostname" : "lion.cdh-bootcamp-bb",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "0e31af0c-6c1c-4180-af2a-3533d5dafab2",
    "ipAddress" : "10.3.12.7",
    "hostname" : "monkey.cdh-bootcamp-bb",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "77736adb-bc63-4161-9ba0-d852b2658b00",
    "ipAddress" : "10.3.12.6",
    "hostname" : "tiger.cdh-bootcamp-bb",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-6d4aa3a506c22f454f973e085391dc6b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "de072d23ab936bfe58dda0a276b8caaa713aa4f284d9a9b9fc03aa01db18e25b",
    "pwSalt" : -4245184567818784056,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-6d4aa3a506c22f454f973e085391dc6b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "621430afff5356b6e9d892c7d24895f27dc14534ef7cdae304404877ce2f3053",
    "pwSalt" : 955545877823610102,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-6d4aa3a506c22f454f973e085391dc6b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "995107072f1c808fed01128ad09093a26422b228db8d3c208ea00d85c10ae650",
    "pwSalt" : 3333993316809172791,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-6d4aa3a506c22f454f973e085391dc6b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "afaa804cf8aa5d7d8fc22a347db404f7e048e172b28b7b3d04f7955ed32caff2",
    "pwSalt" : 4741738180516788893,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-6d4aa3a506c22f454f973e085391dc6b",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "28d968ce1bedaacb70ecddc19ed632cd82e5a2208e3e510e4b8a023d0646452a",
    "pwSalt" : 556820041006147887,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "6d447876261e4d11465912d5e563fa4a00bbaf5c17f8371b22506ee8191adc90",
    "pwSalt" : 9194650499870195812,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "837ceb098a532cc618c593c631743e4defd5011cec3b00fa76e40b42db6a143e",
    "pwSalt" : 4826129289420320524,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170627-1506",
    "gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "lion.cdh-bootcamp-bb"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "password"
        }, {
          "name" : "firehose_database_user",
          "value" : "amonuser"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "lion.cdh-bootcamp-bb"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rmanuser"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "54voc5m3ozke3qopke1vi2ide"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "bd1vhztpspd8z5o47bzwrpsy8"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9erj1w086zfgu2vdsy7dso81d"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "176mz9jf1flkvxkkcrzdoyu0x"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "c1lpmjl3nli02suykll4knajf"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-6d4aa3a506c22f454f973e085391dc6b",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "1551bbc8-8c30-453a-bac6-30188c933f57"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "d2905mhxem0sknuzdktlupf3q"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/23/2012 6:00"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "NOT_ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```