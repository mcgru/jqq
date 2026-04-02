
## Example usage:

Suppose we have `ex3.json` file and we need to make some changes to it.

First, transform it into greppable text format:

```
./jqq -g < ex3.json > ex3.grep
```

Second, make some changes to `ex3.grep` (for example, change values, add leafs and array elements ).

Third, transform new greppable text-file back into json:
```
./jqq -j < ex3.grep > ex4.json
```

## See results:

Changes in greppable-formatted text file:

```
--- ex1.grep    2026-04-02 23:37:35.920087024 +0700
+++ ex2.grep    2026-04-02 23:38:28.005072356 +0700
@@ -7,11 +7,12 @@
 deployment.items.common.properties.dbconnections4      string  2
 deployment.items.common.enableGcLogging        null    null
 deployment.items.instances.0.id        string  1
-deployment.items.instances.0.db.prefix string  pppppp1111111
+deployment.items.instances.0.db.prefix string  pppppp2222
 deployment.items.instances.0.db.userPassword   null    null
 deployment.items.instances.0.properties."mail.smtp.host"       string  mail.gooooogle.com
 deployment.items.instances.0.properties."service.DispatcherService.testMode"   string  true
 deployment.items.instances.1.id        string  2
+deployment.items.instances.2.id        string  3
 deployment.web.common.port     number  8080
 deployment.web.common.jmxPort  null    null
 deployment.web.common.otherJavaProperties      string  asdasdasd
@@ -21,3 +22,6 @@
 deployment.web.instances.1.id  string  2
 deployment.web.instances.2.id  string  3
 otherinfo      string  example
+
+deployment.id  string  my68
+
```

After run `./jqq -j < ex2.grep > ex2.json` we'll get these changes in json:

```
--- ex1.json    2026-04-02 23:37:10.481092138 +0700
+++ ex2.json    2026-04-02 23:38:39.742068320 +0700
@@ -1,6 +1,6 @@
 {
   "deployment": {
-    "id": "my67",
+    "id": "my68",
     "vendor": "myvendor",
     "regressionTest": false,
     "items": {
@@ -19,7 +19,7 @@
         {
           "id": "1",
           "db": {
-            "prefix": "pppppp1111111",
+            "prefix": "pppppp2222",
             "userPassword": null
           },
           "properties": {
@@ -29,13 +29,15 @@
         },
         {
           "id": "2"
+        },
+        {
+          "id": "3"
         }
       ]
     },
     "web": {
       "common": {
         "port": 8080,
-        "webapps": [],
         "jmxPort": null,
         "otherJavaProperties": "asdasdasd"
       },
```
