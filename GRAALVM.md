Some quick 'n' dirty changes in `build.gradle`. It's best to use diff to show the adjustments.

Out of sheer laziness build a fat jar of ilivalidator:
```
gradle clean build shadowJar
```

Build native image:
```
native-image --no-server --verbose --report-unsupported-elements-at-runtime --native-image-info -cp build/libs/ilivalidator-1.11.7-SNAPSHOT-all.jar -H:+ReportExceptionStackTraces
```

Run ilivalidator:
```
./ilivalidator /Users/stefan/Downloads/ch.so.agi.av-gb-administrative-einteilung.xtf
./ilivalidator 254900.itf
```

Seems to be slower than Java. Especially the `first validation pass...` part. No idea why...