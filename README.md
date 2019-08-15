### zt-exec
---
https://github.com/zeroturnaround/zt-exec

```java
new ProcessExecutor().command("java", "-version").execute();

int exit = new ProcessExcutor().command("java", "-version")
  .execute().getExitValue();
  
String output = new ProcessExecutor().command("java", "-version")
  .readOutput(true).execute()
  .outputUTF8();
  
new ProcessExecutor().command("java", "-version")
  .redirectOutput(Slf4Stream.of(LoggerFactory.getLogger(getClass().getName() + ".MyProcess")).asInfo()).execute();
  
new ProcessExecutor().command("java", "-version")
  .redirectOutput(Slf4Stream.of("MyProcess").asInfo()).execute();
  
new ProcessExecutor().comand("java", "-version")
  .redirectOutput(Slf4jStream.ofCaller().asInfo()).execute();
  
String output = new ProcessExecutor().command("java", "-version")
  .redirectOutput(Slf4jStream.of(getClass()).asInfo())
  .readOutput(true).execute().outputUTF8();

String output = new ProcessExecutor().command("java", "-version")
  .redirectError(Slf4jStream.of(getClass()).asInfo())
  .readOutput(true).execute()
  .outputUTF8();
  
try {
  new ProcssExecutor().command("java", "-version")
    .timeout(60, TimeUnit.SECONDS).execute();
}
catch (TimeoutExeption e) {
  //
}

OutputStream out = ...;
new ProcessExecutor().command("java", "-version")
  .redirectOutput(out).execute();
  
new ProcessExecutor().command("java", "-version")
  .redirectOutput(new LogOutputSteam() {
    @Override
    protected void processLine(String line) {
    }
  })
  .execute();

new ProcessExecutor().command("java", "-version").destroyOnExit().execute();

new ProcessExecutor().command("java", "-version")
  .environment("foo", "bar").execute();

Map<String, String> env = ...
new ProcessExecutor().command("java", "-version")
  .environment(env).execute();
  
try {
  new ProcessExecutor().command("java", "-version")
    .exitValues(3).execute();
}
catch(InvalidExitValueException e) {
  System.out.println("Process exited with " + e.getExitValue());
}

String output;
boolean success = false;
try {
  output = new ProcessExecutor().command("java", "-version")
    .readOutput(true).exitValues(3)
    .execute().outputUTF8();
}
catch (InvalidExitValueException e) {
  System.out.println("Process exited with " + e.getExitValue());
  output = e.getResult().outputUTF8();
}

Future<ProcessResult> future = new ProcessExecutor()
  .command("java", "-version")
  .start().getFuture();
  
Future<ProcessResult> future = new ProcessExecutor()
  .command("java", "-version")
  .readOutput(true)
  .start().getFuture();
  
String ouptut = future.get(60, TimeUnit.SECONDS).outputUTF8();
```

```
```

```
```
