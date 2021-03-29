# IBM Cloud Foundry - XRay

Use GitHub Actions to automatically deploy the latest version of XRay to IBM Cloud Foundry

[Read the details in my blog (in Chinese) | 中文教程](https://p3terx.com/archives/how-to-use-ibm-cloud-gracefully-for-free.html)

## Usage

- Click the [Use this template](https://github.com/P3TERX/IBM-CF-V2/generate) button to create a new repository.
- Click the `Settings` tab on your own repository, and then click the `Secrets` button to add the following encrypted environment variables:

  | Environment Variables | Description |
  | --------------------- | ----------- |
  | `IBM_CF_USERNAME`       | IBM Cloud user name (email address) |
  | `IBM_CF_PASSWORD` | IBM Cloud password |
  | `IBM_CF_ORG_NAME`(optional) | Organization name, the default is the email address. Can be found on [this page](https://cloud.ibm.com/account/cloud-foundry). |
  | `IBM_CF_SPACE_NAME`(optional) | Space name, default is `dev`. Can be found on [this page](https://cloud.ibm.com/account/cloud-foundry). |
  | `IBM_CF_APP_NAME` | App name, fill in according to your preference. |
  | `XR_VM_UUID` </br> `XR_VL_UUID` | Generate using UUID generator, also selected VMess and VLESS and Trojan, include path, Choose 1 from 2 options. |

- Click the `Run workflow` button on the Actions page.
- Wait for the deployment to complete.
- Click the relevant application on the [Cloud Foundry Public](https://cloud.ibm.com/cloudfoundry/public) page to view the access address.

> **TIPS:** You can customize the API address and App memory size through the workflow file.

## Acknowledgments

- [Project V](https://github.com/v2ray/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [IBM Cloud](https://cloud.ibm.com/)
- [GitHub Actions](https://github.com/features/actions)
- [Better Cloudflare IP](https://github.com/XIU2/CloudflareSpeedTest.git)

## VM/VL Client Setup

| Client Variables | Values |
  | ---------------- | ------ |
  | `Address` | ${IBM_CF_APP_NAME}.us-south.cf.appdomain.cloud </br> Cloudflare Reverse Proxy IP |
  | `Port` | 443 |
  | `VM/VL User ID` | XR_VM_UUID </br> XR_VL_UUID |
  | `Flow` | xtls-rprx-direct |
  | `Network` | ws </br> websocket |
  | `Host` | ${IBM_CF_APP_NAME}.us-south.cf.appdomain.cloud </br> Cloudflare Reverse Proxy Domain Name |
  | `Type` | none |
  | `Path` | /${XR_VM_UUID}-vmess </br> /${XR_VL_UUID}-vless |
  | `Tls` | Tls must open, otherwise you will be disconnected |
  | `AllowInsecure` | false |
  | `SNI` | Same as Host |

## Client Ws+Tls+Xtls-rprx-direct(Flow) Support Status

| Client | Status |
| ------ | ------ |
| `2dust V2RayN` </br> `2dust V2RayNG` | Ws+Tls+Flow |
| `OpenWrt SSRPlus` | Ws+Tls |
| `OpenWrt Passwall` | Ws+Tls |
| `QV2Ray` | Ws+Tls |

## Cloudflare Reverse Proxy Code

```
const SingleDay = '${IBM_CF_APP_NAME}.us-south.cf.appdomain.cloud'
const DoubleDay = '${IBM_CF_APP_NAME}.us-south.cf.appdomain.cloud'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname="${IBM_CF_APP_NAME}.us-south.cf.appdomain.cloud";
        url.pathname="";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

## Licence

[MIT](https://github.com/P3TERX/IBM-CF-V2/blob/main/LICENSE) © P3TERX

## 重要信息

fork或clone本项目请低调使用，执意在任何网站上宣传并且不同意低调使用的请立刻关闭本页面离开！！！

严禁任何网友在任何网站上宣传，否则产生的一切后果自行承担！！！

感谢P3TERX提供原项目

- [IBM-CF-V2](https://github.com/P3TERX/IBM-CF-V2.git)

重要的事情说三遍，不要设置Action自动重启。因此设置导致的一切后果本人概不负责！！！

只要还在使用ibm xray搭建的节点，节点超过10天是不会自动关闭的。

禁止滥用，因滥用产生的一切后果本人概不负责！！！

本项目自2021.3.29之后不再更新，因用的人太多，项目被封。不再维护该项目。

## Important information

Fork or clone this project, please use it in a low-key manner. If you insist on advertising on any website and do not agree with the low-key use, please close this page and leave immediately! ! !

It is strictly forbidden for any netizens to advertise on any website, otherwise all the consequences will be borne by themselves! ! !

Thank P3TERX for providing the original project

- [IBM-CF-V2](https://github.com/P3TERX/IBM-CF-V2.git)

The important thing is said three times, do not set the Action to automatically restart. Therefore, I am not responsible for all consequences caused by the setting! ! !

As long as the node built with ibm xray is still used, the node will not be automatically closed for more than 10 days.

Abuse is prohibited, I am not responsible for any consequences arising from abuse! ! !

This project will no longer be updated after 2021.3.29. Because there are too many people using it, the project has been blocked. The project is no longer maintained.

## 重要な情報

このプロジェクトをフォークまたはクローンする場合は、控えめに使用してください。Webサイトでの広告を主張し、控えめな使用に同意しない場合は、このページを閉じてすぐに終了してください。 ！ ！ ！

ネチズンがウェブサイトで宣伝することは固く禁じられています。そうしないと、すべての結果は自分で負担することになります。 ！ ！ ！

元のプロジェクトを提供してくれてありがとうP3TERX

- [IBM-CF-V2](https://github.com/P3TERX/IBM-CF-V2.git)

重要なことは3回言われていますが、自動的に再起動するようにアクションを設定しないでください。 したがって、私は設定によって引き起こされるすべての結果に対して責任を負いません！ ！ ！

ibm xrayで構築されたノードが引き続き使用されている限り、ノードは10日を超えて自動的に閉じられません。

虐待は禁止されています、私は虐待から生じるいかなる結果に対しても責任を負いません！ ！ ！

このプロジェクトは2021.3.29以降更新されなくなります。使用する人が多すぎるため、プロジェクトはブロックされました。 プロジェクトはもはや維持されていません。
