# Chạy profile `cloud` bằng CLI

Có hai cách.

## Cách 1 — Không sửa `application.properties`

Đây là cách **khuyến nghị** khi chỉ muốn test cloud một lần.

PowerShell:

```powershell
$env:OPENROUTER_API_KEY="YOUR_API_KEY"

.\gradlew.bat bootRun --args="--spring.profiles.active=cloud"
```

Spring Boot sẽ override:

```properties
spring.profiles.active=local
```

bằng:

```text
cloud
```

Luồng chạy:

```text
CLI
 ↓
--spring.profiles.active=cloud
 ↓
application-cloud.properties
 ↓
OpenRouter
 ↓
Gemini 2.5 Flash
```

## Cách 2 — Đổi mặc định sang cloud

Trong:

```properties
application.properties
```

đổi:

```properties
spring.profiles.active=local
```

thành:

```properties
spring.profiles.active=cloud
```

Sau đó:

```powershell
$env:OPENROUTER_API_KEY="YOUR_API_KEY"

.\gradlew.bat bootRun
```