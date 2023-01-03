---
title: "Operator"
date: 2022-12-28T20:51:18+08:00
draft: true
---

1. Reconcile 默认每 10 hours 被 触发一次
```
syncPeriod := time.Duration(10 * time.Hour)
	mgr, err := ctrl.NewManager(ctrl.GetConfigOrDie(), ctrl.Options{
		Scheme:                 scheme,
		MetricsBindAddress:     metricsAddr,
		Port:                   9443,
		HealthProbeBindAddress: probeAddr,
		LeaderElection:         enableLeaderElection,
		LeaderElectionID:       "1d3ba712.longbridge-inc.com",
		SyncPeriod:             &syncPeriod,
	})
```
2. EventFilter 是全局的，即便在其中一个 controller 中 执行 **WithEventFilter** ,对同一个 operator 下的所有 controller 生效。与 role 类似，因为只有一个 sa.