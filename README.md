# Grafana Permission Denied
Grafana 容器在嘗試創建 `/var/lib/grafana/plugins` 目錄時遇到了權限問題，並且顯示 `/var/lib/grafana` 目錄不可寫。
這通常是因為宿主機上的掛載目錄 `(./grafana)` 權限不足，導致容器無法寫入數據。
# Solution
檢查宿主機目錄的權限
`ls -ld ./grafana`
目錄不存在，可以手動創建
`mkdir -p ./grafana`
修改目錄的擁有者和權限
`sudo chown -R 472:472 ./grafana`
重新啟用`docker-compose`