# IBM Cloud Foundry - XRay

Use GitHub Actions to automatically deploy the latest version of V2Ray to IBM Cloud Foundry

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
  | `XR_UUID` | Generate using UUID generator |
  | `XR_WS_PATH_VMESS` </br> `XR_WS_PATH_VLESS` | Select one of the VMess and VLESS protocols, and fill in a combination of numbers and English letters. |

- Click the `Run workflow` button on the Actions page.
- Wait for the deployment to complete.
- Click the relevant application on the [Cloud Foundry Public](https://cloud.ibm.com/cloudfoundry/public) page to view the access address.

> **TIPS:** You can customize the API address and App memory size through the workflow file.

## Acknowledgments

- [Project V](https://github.com/v2ray/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [IBM Cloud](https://cloud.ibm.com/)
- [GitHub Actions](https://github.com/features/actions)

## Licence

[MIT](https://github.com/P3TERX/IBM-CF-V2/blob/main/LICENSE) © P3TERX

## 重要信息

fork或clone本项目请低调使用，执意要在youtube和bilibili上宣传和不同意低调使用的请立刻关闭本页面离开！！！

Fork or clone this project, please use it in a low-key manner. If you insist on advertising on youtube and bilibili and do not agree with it, please close this page and leave immediately! ! !

禁止在youtube和bilibili上宣传，后果很严重！！！

It is forbidden to promote on youtube and bilibili, the consequences are serious! ! !

因在youtube和bilibili上宣传出现任何问题，后果自负！！！

Any problems in the promotion on youtube and bilibili are at your own risk! ! !

fork之后请自觉注明P3TERX/IBM-CF-V2链接！！！

Please consciously indicate the P3TERX/IBM-CF-V2 link after fork！！！

- [IBM-CF-V2](https://github.com/P3TERX/IBM-CF-V2.git)

感谢P3TERX提供原项目

Thank P3TERX for providing the original project

- [IBM-CF-V2](https://github.com/P3TERX/IBM-CF-V2.git)
