# Nextcloud Helm Chart

## Предварительные требования
1. Убедитесь, что в кластере созданы следующие Secrets в namespace `nextcloud`:
   - **Имя секрета**: `nextcloud-secrets`
   - **Ключи**:
     - `POSTGRES_DB`
     - `POSTGRES_USER`
     - `POSTGRES_PASSWORD`
     - `NEXTCLOUD_ADMIN_USER`
     - `NEXTCLOUD_ADMIN_PASSWORD`

2. Рекомендуется использовать [Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets) для безопасного хранения секретов.

## Пример создания Secrets
Создайте файл `secrets.yaml`:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: nextcloud-secrets
  namespace: nextcloud
type: Opaque
data:
  POSTGRES_DB: <base64-encoded-value>
  POSTGRES_USER: <base64-encoded-value>
  POSTGRES_PASSWORD: <base64-encoded-value>
  NEXTCLOUD_ADMIN_USER: <base64-encoded-value>
  NEXTCLOUD_ADMIN_PASSWORD: <base64-encoded-value>