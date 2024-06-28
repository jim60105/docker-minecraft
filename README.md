# docker-minecraft

這是我用於運行個人 Minecraft 伺服器的 docker compose 專案。  
此專案是為了我的個人需求而撰寫，並抽出敏感資訊和設定。

請自行調整它以符合您的需求。

## 特色

- 使用[容器化的 Minecraft 伺服器](https://hub.docker.com/r/itzg/minecraft-server)，便於部署和管理。
- 以 4GB RAM + 12GB Swap 設計配置伺服器。
- 包含了以下 Minecraft 插件
  - [CoreProtect](https://www.spigotmc.org/resources/coreprotect.8631/)
  - [Chunky](https://modrinth.com/plugin/chunky)
  - [VillagerGPT](https://github.com/jim60105/VillagerGPT-zh)
- 支持 S3 自動備份和恢復功能。
- 將日誌輸出到 Seq 以便進行日誌管理。
- Podman 友善。

## 硬體需求

- 4GB RAM + 12GB Swap
- 2 CPU Core (minecraft 本身僅使用 1 Core，但 2 Core 能讓伺服器主體流暢運行)
- 需要安裝 Docker 和 Docker Compose。
- 需要一個(外部) S3 存儲體來存儲備份。
- 需要一個(外部) Seq 伺服器來接收日誌。

## 快速開始

1. 修改 `.env_sample` 文件：
    - 將 `.env_sample` 文件複製為 `.env`。
    - 修改 `.env` 文件中的相關環境變量。
2. 修改 `plugins\VillagerGPT\config.yml_sample` 文件：
    - 將 `plugins\VillagerGPT\config.yml_sample` 文件複製為 `config.yml`。
    - [參考此文件](https://github.com/jim60105/VillagerGPT-zh?tab=readme-ov-file#%E8%A8%AD%E5%AE%9A)修改 `config.yml` 文件中的設定。
3. （可選）配置 `docker-compose.restore.yml` 以恢復備份。
4. 運行 `docker-compose up -d` 啟動伺服器。

## 備份和恢復

- 備份配置在 `docker-compose.yml` 中的 `backups` 服務中定義。
- 使用 `docker-compose -f docker-compose.restore.yml up` 進行恢復。

## LICENSE

> [!NOTE]  
> Please refer to the license files for each container image and plugin used in this project.  
> The following is the license for the docker compose files and setting files in this repository.

<img src="https://github.com/jim60105/docker-minecraft/assets/16995691/df3fe810-c619-46b0-9e82-ab7e597e545f" alt="agplv3" width="300" />

[GNU AFFERO GENERAL PUBLIC LICENSE Version 3](/LICENSE)

This program is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.
