https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1190  (platformcolor)

https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1131     flexDirection is set to "row-reverse,"
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1099  axios传中文的问题
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1167 RNViewBase居中的问题
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1113   ClipPathView问题



RN平台， JsBundle通过hermesc工具转码后，性能明显提升，但是连续频繁加载hbc文件，容易出现AppCrash
Device info:HUAWEI Mate 60 Pro
Build info:ALN-AL00 5.0.0.26(SP8DEVC00E29R4P6log)
Fingerprint:7be2747b63e28fbc3465ad972fd7fbf02368cda64427348f192bfba72c53babb
Module name:com.autohome.main
Version:0.9.1
VersionCode:1000010
PreInstalled:No
Foreground:No
Timestamp:2024-07-17 10:07:23.279
Pid:48982
Uid:20020054
Process name:com.autohome.main
Process life time:640s
Reason:Signal:SIGSEGV(SEGV_MAPERR)@000000000000000000  probably caused by NULL pointer dereference
Fault thread info:
Tid:53535, Name:RNOH_JS
#00 pc 0000000000077fa0 /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#01 pc 000000000023cf84 /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#02 pc 000000000023d060 /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#03 pc 0000000000229bd4 /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#04 pc 0000000000107dbc /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#05 pc 00000000000edd14 /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#06 pc 00000000000868cc /data/storage/el1/bundle/libs/arm64/libhermes.so(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#07 pc 000000000007f5d8 /data/storage/el1/bundle/libs/arm64/libhermes.so(facebook::hermes::makeHermesRuntime(hermes::vm::RuntimeConfig const&)+60)(a2d5c4b683181ee46ec43424086c7624fabcecf7)
#08 pc 00000000008b0928 /data/storage/el1/bundle/libs/arm64/librnoh.so(facebook::react::HermesExecutorFactory::createJSExecutor(std::__n1::shared_ptr<facebook::react::ExecutorDelegate>, std::__n1::shared_ptr<facebook::react::MessageQueueThread>)+96)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#09 pc 0000000000892f68 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#10 pc 000000000087b35c /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#11 pc 000000000087b13c /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#12 pc 000000000087afec /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#13 pc 000000000087aea8 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#14 pc 000000000087ae3c /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#15 pc 000000000087adf4 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#16 pc 000000000087add0 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#17 pc 0000000000879dd0 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#18 pc 000000000064ff8c /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__value_func<void ()>::operator()[abi:v15004]() const+64)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#19 pc 000000000064fadc /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::function<void ()>::operator()() const+20)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#20 pc 000000000075faf0 /data/storage/el1/bundle/libs/arm64/librnoh.so(rnoh::TaskExecutor::runSyncTask(rnoh::TaskThread, std::__n1::function<void ()>&&)::$_2::operator()() const+40)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#21 pc 000000000075fab8 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#22 pc 000000000075fa70 /data/storage/el1/bundle/libs/arm64/librnoh.so(void std::__n1::__invoke_void_return_wrapper<void, true>::__call<rnoh::TaskExecutor::runSyncTask(rnoh::TaskThread, std::__n1::function<void ()>&&)::$_2&>(rnoh::TaskExecutor::runSyncTask(rnoh::TaskThread, std::__n1::function<void ()>&&)::$_2&)+20)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#23 pc 000000000075fa4c /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#24 pc 000000000075e9a8 /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__func<rnoh::TaskExecutor::runSyncTask(rnoh::TaskThread, std::__n1::function<void ()>&&)::$_2, std::__n1::allocator<rnoh::TaskExecutor::runSyncTask(rnoh::TaskThread, std::__n1::function<void ()>&&)::$_2>, void ()>::operator()()+24)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#25 pc 000000000064ff8c /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__value_func<void ()>::operator()[abi:v15004]() const+64)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#26 pc 000000000064fadc /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::function<void ()>::operator()() const+20)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#27 pc 000000000076958c /data/storage/el1/bundle/libs/arm64/librnoh.so(rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0::operator()() const+24)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#28 pc 0000000000769564 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#29 pc 000000000076951c /data/storage/el1/bundle/libs/arm64/librnoh.so(void std::__n1::__invoke_void_return_wrapper<void, true>::__call<rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0&>(rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0&)+20)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#30 pc 00000000007694f8 /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__alloc_func<rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0, std::__n1::allocator<rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0>, void ()>::operator()[abi:v15004]()+24)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#31 pc 0000000000768578 /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__func<rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0, std::__n1::allocator<rnoh::ThreadTaskRunner::runSyncTask(std::__n1::function<void ()>&&)::$_0>, void ()>::operator()()+24)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#32 pc 000000000064ff8c /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::__function::__value_func<void ()>::operator()[abi:v15004]() const+64)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#33 pc 000000000064fadc /data/storage/el1/bundle/libs/arm64/librnoh.so(std::__n1::function<void ()>::operator()() const+20)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#34 pc 00000000007675ec /data/storage/el1/bundle/libs/arm64/librnoh.so(rnoh::ThreadTaskRunner::runLoop()+264)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#35 pc 0000000000769db4 /data/storage/el1/bundle/libs/arm64/librnoh.so(rnoh::ThreadTaskRunner::ThreadTaskRunner(std::__n1::basic_string<char, std::__n1::char_traits<char>, std::__n1::allocator<char>>, std::__n1::function<void (std::exception_ptr)>)::$_1::operator()() const+24)(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#36 pc 0000000000769d64 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#37 pc 0000000000769d00 /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#38 pc 00000000007697fc /data/storage/el1/bundle/libs/arm64/librnoh.so(8ce2efe2e21d8cd33f94ed6e68876cdc5adfdbfc)
#39 pc 00000000001b8e54 /system/lib/ld-musl-aarch64.so.1(start+236)(5eee310927fa497814a95d97820a89bb)
Registers:
x0:0000000000000000 x1:0000005b87545af0 x2:0000000000000000 x3:3d2065756c617628
x4:203d2079726f6765 x5:0000005b7af5aef9 x6:6f756769746e6f43 x7:61726f7473207375
x8:0000000000000000 x9:000000000000002a x10:2c636972656e6567 x11:6567617373656d20
x12:6120646142203d20 x13:0029737365726464 x14:65203a2e64656c69 x15:646f635f726f7272
x16:2065756c61762865 x17:6163202c3431203d x18:ffff000000000006 x19:0000005b87545b88
x20:0000000000000001 x21:0000000000000000 x22:0000005b15ad9a28 x23:0000005b158f7f84
x24:00000000c0000000 x25:0000005b875469a0 x26:0000005b87546990 x27:0000005b87546980
x28:00000059ecbc22c0 x29:0000005b87545b40
lr:0000005b15abcf88 sp:0000005b87545ac0 pc:0000005b158f7fa0
Other thread info:
Tid:48982, Name:m.autohome.main
#00 pc 00000000001b4740 /system/lib/ld-musl-aarch64.so.1(__timedwait_cp+192)(5eee310927fa497814a95d97820a89bb)
#01 pc 00000000001ba80c /system/lib/ld-musl-aarch64.so.1(__pthread_mutex_timedlock_inner+592)(5eee310927fa497814a95d97820a89bb)
#02 pc 00000000001de408 /system/lib/ld-musl-aarch64.so.1(PauseMainThreadHandler+76)(5eee310927fa497814a95d97820a89bb)
#03 pc 0000000000001974 shmm
#04 pc 00000000000013e8 shmm
#05 pc 00000000001b4738 /system/lib/ld-musl-aarch64.so.1(__timedwait_cp+184)(5eee310927fa497814a95d97820a89bb)
