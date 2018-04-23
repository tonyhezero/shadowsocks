# Chrome + Proxy SwitchyOmega 设置

這裏假設您已經配置好 Shadowsocks 客戶端，具體請參考

[Windows 下安裝配置 Shadowsocks 使用教程](https://github.com/Shadowsocks-Wiki/shadowsocks/blob/master/2-windows-settings.md)

[macOS 下安裝配置 Shadowsocks 使用教程](https://github.com/Shadowsocks-Wiki/shadowsocks/blob/master/3-macos-settings.md)

[Linux 下安裝配置 Shadowsocks 使用教程](https://github.com/Shadowsocks-Wiki/shadowsocks/blob/master/6-linux-settings.md)

注：本文并不適合任何手機上的 Firefox 瀏覽器  

## 1、安裝擴展

您可以通過chrome商店安裝 [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/padekgcemlokbadohgkifijomclgjgif) 擴展

如果無法訪問，您也可以直接在 [Github](https://github.com/FelisCatus/SwitchyOmega/releases) 下載 .crx 文件并拖入 `chrome://extensions/` （請使用 Chrome 瀏覽器複製粘貼輸入地址欄並回車訪問）

本擴展同樣適用于 Firefox 57 (Firefox Quantum) 以上版本: 安裝鏈接 [Proxy SwitchyOmega](https://addons.mozilla.org/zh-CN/firefox/addon/switchyomega/)

## 2、擴展的配置(配合 GFWlist 實現自動區分流量)

### 1、可以直接使用本站提供的已經設置好的備份直接恢復配置（推薦）

通過這個鏈接下載 switchyomega 的配置文件

Shadowsocks 客戶端本地 socks 端口為 1080 的可以下載: [SwitchOmega + GFWList 自动切换配置文件[1080]](https://portal.shadowsocks.to/dl.php?type=d&id=74)  
（適用於 Shadowsocks-Windows / Linux / ShadowsocksX(macOS) 等默認端口為 1080 的客戶端）

macOS 下的 ShadowscoksX-NG 默認本地端口為 1086 可以下載：[ SwitchOmega + GFWList 自动切换配置文件[1086]](https://portal.shadowsocks.to/dl.php?type=d&id=75)  

然後打開 `Proxy SwitchyOmega` 的設置，選擇從備份文件恢復，然後選擇剛才下載的文件，如圖

![](https://ooo.0o0.ooo/2016/06/22/576a3a86d866b.png)

這時點擊 Chrome 地址欄 中的 `switchyomega` 圖標，可以看到有四個模式

```
直接連接
系統代理
Shadowsocks
自動切換
```
幾個模式的區別，當你的代理模式選中

1. **直接連接**：所有訪問都不經過代理  
2. **系統代理**：訪問網站與系統的默認代理有關  
3. **Shadowsocks**：擴展自身控制，所有訪問都經過代理  
4. **自動切換**：擴展自身控制，根據規則區分網站是否經過代理，本站提供的配置使用 GFWList 控制，包含了大部分無法直接訪問的網站默認經過代理，可以直接連接的網站則不經過代理，推薦日常使用，在本文底部可以查看如何自定義配置規則

#### 自定義規則  

在自動切換模式點擊添加條件：

條件類型選擇： `域名通配符`    
條件設置填寫： `*.域名`  
情景模式： 選 `Shadowsocks` 則經過代理， 選 ` 直接連接` 則不經過代理  

![自定義規則示例](https://i.loli.net/2018/04/23/5add7ff19ddfd.png)

**（如果使用了本站提供的配置文件，請忽視下面的內容）**

### 2、手動設置

按照下圖所示

1. 單擊新建情景模式，在彈出的窗口中選中自動切換，並且將名稱填寫為自動切換或其他名稱
2. 在新的頁面，首先單擊添加在線規則
![](https://ooo.0o0.ooo/2016/06/22/576aaba960469.png)
3. 將規則列表規則對應的 ③ 的位置地方選為 Shadowsocks 對應的規則，如果之前是導入本站的備份的話，請選中 ss 即可。
4. 將規則列表格式選中 AutoProxy
5. 在規則列表網址中填入
`https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt`

![](https://ooo.0o0.ooo/2016/06/22/576aa998042f0.png)

之後可以可以通過選中該模式實現自動代理，如果特殊需要的域名也可以手動通過添加條件指定代理
