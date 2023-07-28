---
title: bingo
emoji: 📉
colorFrom: red
colorTo: red
sdk: docker
pinned: true
license: mit
---

<div align="center">

# Bingo 

Bingo，一个让你呼吸顺畅 New Bing。

高度还原 New Bing 网页版的主要操作，国内可用，兼容绝大多数微软 Bing AI 的功能，可自行部署使用。

[![MIT License](https://img.shields.io/badge/license-MIT-97c50f)](https://github.com/weaigc/bingo/blob/main/license)


</div>

## 演示站点

 * 站点一：https://bing.github1s.tk （推荐）
 * 站点二：https://effulgent-bubblegum-e2f5df.netlify.app （此站点部署到 Netlify 上）


[![img](./docs/images/demo.png)](https://bing.github1s.tk)

## 功能和特点

- 完全基于 Next.js 重写，高度还原 New Bing Web 版 UI，使用体验和 Bing AI 基本一致。
- 支持 Docker 构建，方便快捷地部署和访问。
- Cookie 可全局配置，全局共享。
- 支持持续语音对话

## RoadMap

 - [x] 支持 wss 转发
 - [x] 支持一键部署
 - [x] 优化移动端展示
 - [x] 支持画图
 - [x] 支持语音输入(支持语音指令，目前仅支持 PC 版 Edge 及 Chrome 浏览器)
 - [x] 支持语音输出(需要手动开启)
 - [ ] 适配深色模式
 - [ ] 支持内置提示词
 - [ ] 支持图片输入
 - [ ] 支持离线访问
 - [ ] 国际化翻译

## 一键部署
你也可以一键部署自己的 New Bing AI 到 🤗 HuggingFace 。

### 部署到 Huggingface
[![Deploy to HuggingFace](https://img.shields.io/badge/%E7%82%B9%E5%87%BB%E9%83%A8%E7%BD%B2-%F0%9F%A4%97-fff)](https://huggingface.co/login?next=%2Fspaces%2Fhf4all%2Fbingo%3Fduplicate%3Dtrue%26visibility%3Dpublic)

> Huggingface 不支持绑定自己的域名，不过我们可以使用曲线救国的方式来达到这个目的
1. 方式一，借助 Github Pages 及 iframe [如何绑定域名](https://github.com/weaigc/bingo/issues/4)
2. 方式二，Cloudflare Workers 

### 其它平台
由于其他平台目前遭到 new bing 封杀，会遇到更多问题，不再做推荐，建议直接使用上面的方式。
#### 部署到 Netlify
[![Deploy to Netlify Button](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/weaigc/bingo)

#### 部署到 Vercel
如果你是 Vercel 付费用户，可以点以下链接一键部署到 Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?demo-title=bingo&demo-description=bingo&demo-url=https%3A%2F%2Fbing.github1s.tk%2F&project-name=bingo&repository-name=bingo&repository-url=https%3A%2F%2Fgithub.com%2Fweaigc%2Fbingo&from=templates&skippable-integrations=1&env=BING_HEADER&envDescription=%E5%A6%82%E6%9E%9C%E4%B8%8D%E7%9F%A5%E9%81%93%E6%80%8E%E4%B9%88%E9%85%8D%E7%BD%AE%E8%AF%B7%E7%82%B9%E5%8F%B3%E4%BE%A7Learn+More&envLink=https%3A%2F%2Fgithub.com%2Fweaigc%2Fbingo%2Fblob%2Fmain%2F.env.example)

#### 部署到 Render

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/weaigc/bingo)


## 环境和依赖

- Node.js >= 18
- Bing AI 的 Cookie (前往 https://www.bing.com/ ，登录，然后[找到 bing.com 域名下的一个名叫 _U 的 Cookie 的值](#如何获取-cookie))

## 安装和使用

* 使用 Node 启动

```bash
git clone https://github.com/weaigc/bingo.git
npm i # 推荐使用 pnpm i
npm run build
npm run start
```

* 使用 Docker 启动
```bash
git clone https://github.com/weaigc/bingo.git
docker build . -t bingo
docker run --rm -it -e BING_HEADER=xxxx -p 7860:7860 bingo
```

## 如何获取 BING_HEADER
![BING HEADER](./docs/images/curl.png)

> 复制出来的内容应该如下所示:
```
curl 'https://www.bing.com/turing/conversation/create' \
  -H 'authority: www.bing.com' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6' \
  -H 'cache-control: max-age=0' \
  -H 'cookie: MicrosoftApplicationsTelemetryDeviceId=3399c004-fd0e-48ec-bb92-d82a27b2bbd4; _EDGE_V=1; SRCHD=AF=NOFORM; SRCHUID=V=2&GUID=29EBDDA4E6674329ACCF1A0A423C3E98&dmnchg=1; _UR=QS=0&TQS=0; _HPVN=CS=eyJQbiI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiUCJ9LCJTYyI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiSCJ9LCJReiI6eyJDbiI6MSwiU3QiOjAsIlFzIjowLCJQcm9kIjoiVCJ9LCJBcCI6dHJ1ZSwiTXV0ZSI6dHJ1ZSwiTGFkIjoiMjAyMy0wNy0yNVQwMDowMDowMFoiLCJJb3RkIjowLCJHd2IiOjAsIkRmdCI6bnVsbCwiTXZzIjowLCJGbHQiOjAsIkltcCI6Mn0=; _RwBf=ilt=1&ihpd=1&ispd=0&rc=0&rb=0&gb=0&rg=200&pc=0&mtu=0&rbb=0&g=0&cid=&clo=0&v=1&l=2023-07-25T07:00:00.0000000Z&lft=0001-01-01T00:00:00.0000000&aof=0&o=2&p=&c=&t=0&s=0001-01-01T00:00:00.0000000+00:00&ts=2023-07-25T11:00:31.7111548+00:00&rwred=0&wls=&lka=0&lkt=0&TH=&dci=0; ANON=A=0043C6590EA808ED6E395059FFFFFFFF&E=1c8b&W=1; NAP=V=1.9&E=1c31&C=DnaMSbDN_4efZ_xXqBF3Daorjr53kYqYoaP8YHsupjmiXnysX7a37A&W=1; PPLState=1; KievRPSSecAuth=FABSBBRaTOJILtFsMkpLVWSG6AN6C/svRwNmAAAEgAAACMGUA7EGVSjGEAQBGHtNsc5sNL7unmJsfPJ2t6imfo4BeUJlAia3IpMTtMUy4PU/C5QAzRI5pODtsIee0+blgllXt/5IiWwGjwmdhivsFM597pRPkjARPfwsPhNLPNbJrCPNPHdje4Is78MnCADXw6/NBq2FL8V2/byw2fH6IuAMD2MvN/VvqpEa9ZxiDjZtENj4HEj0mO2SgzjfyEhVAkjvznJqU2rw/Q2tHmX94NAM2kzlzKF/hWPhCCUmu8IHLvCnHDS6mSptvJDDP/sp3ovtzOXkP1mlM/Xju5ftesUvccVEQGffXORa1dE5hEMbKIiKXz1tDdduSXE19g9/+mRMAjaQhpwhI8XmilCTx1adb1Ll5qK+VjC9GNfEZzcbsGBPVaOl+anG8rEMq+Xnhjo7J+NqTNolavHgcuV8kJsCeJZIged33UA8eOZeFo+wAECMguxMoSqgpGH+sthqynvD/FJD6r/tiU2N3uqVq8NE8V37asrN6T14Z0FGBJOe6ET1+PGApm3s11OY9/xhFEB9T5BEPUGEbvRcLcW2ncFQX0EU+xweiPqo1Q1hNUg/dCtSI+lZ7c2H8XheePZavZ0TJQ8oNCSAuKiTqJmI0fVGpwbXwfaADkEipuawz3fIuMJBNgMU0OtA7Hm59v2fGLIBuvi6YeKS6GgVk3BIPf+P/eKahwozrxQZaFnoHTSqMkvct7xCP4atBROfXKf5Ww0CcFKp+2WX9BIskTOo2jjk6bAyyYJ+ElUB1fgLKNk5m/YSMc9iYCLIBMIGN8F0Yvy3tZ7cvh7Ue5Klo98US/I+nW1G7ZJMHRgUO8h8lpneHqEMegKd8gynO4VF7RpCjJkunDmW0Ta+RkXAP619pg0dqHMFkoOgknN78oBbGTV6fJUKotv+vi61kLhAeXZGWoHGCRXh2wUC6YgfPgKA6ESRNHtFn7E5B3HHpLc5rVMDSNhKZYfdhupV4Ezf6+5DhMcZLZhi0kk+ivDiN1gdHlVtSN55xpvf+c+XZDzR0uhgcvgy0LAbmzgk6y4WbYH+LQsMpzNNj+aC72vMiWovWrKh9jY4MYCmdgxsS/skPtLdp18muiEIRXTbZQGUmhxFpJAIbBIsCscMpzL0BgeujxUwM5wr79Sd9r4xwbgSMwmBlBfUHRVBdNyg8feepeJbCS63nD6eHOuLqMRsPIio3w/ki/EAa92UUEiZeavLsMUD/y/qAvWUdzdP5Y+C/TM+CMGS/kGL4LEdY/28MQeTvU1qv1X21kQt2aiaj3pPVL36hAzxbcLgqcMo9oymDRy87kdCXW/+g4oKLtMh6fm/G6W6Y/B01JlxohyyvueHQIG557uzkEkTJ3FnOVODSKBKpb3WZ65rExfV71zSZa25F3GmpaIG6HiYrX2YYhQAkIE9pKEQBHbnwHuwNDGottZTXZw=; WLS=C=9df3f9d8518fae19&N=wen; WLID=pGY8HgWCu4p5XYCOk2oa0+DBdftkMUfmNIn8XtSjSTKsgv/Il7GUlYs0Jpjf/E12jZMgV7x44Dy3fXOgjjUoJx7Y/ClLrLhsk20THksJJoI=; _EDGE_S=F=1&SID=17CF6EE006426448213C7DB907436588&mkt=zh-CN; MUID=225621093D8A6C27301632413C0E6D08; MUIDB=225621093D8A6C27301632413C0E6D08; SUID=A; SNRHOP=I=&TS=; _U=nGyzKQruEsDwLiu65fZFIG6e12hf2lwTJmroW__k8joUJIKmG3OIjayXKGW9dCVR3sNhF76mEVxyW6yjUGPodOfjtSa3s3J_DxMOrEK1BqXCOBI9bC66spAIASV7prsYFlVAJz73jVNENp_tBubLHJy6EbT0BKRe4AjrYkH-9uMnmCKB8Zmyg; _SS=SID=17CF6EE006426448213C7DB907436588&R=0&RB=0&GB=0&RG=200&RP=0&PC=U531; SRCHS=PC=U531; USRLOC=HS=1&ELOC=LAT=22.501529693603516|LON=113.9263687133789|N=%E5%8D%97%E5%B1%B1%E5%8C%BA%EF%BC%8C%E5%B9%BF%E4%B8%9C%E7%9C%81|ELT=2|&CLOC=LAT=22.50153029046461|LON=113.92637070632928|A=733.4464586120832|TS=230726151034|SRC=W; SRCHUSR=DOB=20230725&T=1690384908000&POEX=W; ipv6=hit=1690388509974&t=6; SRCHHPGUSR=HV=1690384945&SRCHLANG=zh-Hans&PV=15.0.0&BRW=MW&BRH=MT&CW=410&CH=794&SCW=410&SCH=794&DPR=1.5&UTC=480&DM=0&WTS=63825879627&PRVCW=410&PRVCH=794&PR=1.5; cct=AjWIBYOoVP-Afq6gWwtx80If6yHn6iBuEVHA1XHdAKpny6Y_CVyi_MSyM94VyMWnjdYkkccVtm3czoIAtXUGQA; GC=AjWIBYOoVP-Afq6gWwtx80If6yHn6iBuEVHA1XHdAKpR3Y_D9Ytcks4Ht6XhadXk75dvhzP4YOUS0UmoEyqyxw' \
  -H 'dnt: 1' \
  -H 'sec-ch-ua: "Chromium";v="116", "Not)A;Brand";v="24", "Microsoft Edge";v="116"' \
  -H 'sec-ch-ua-arch: "x86"' \
  -H 'sec-ch-ua-bitness: "64"' \
  -H 'sec-ch-ua-full-version: "116.0.1938.29"' \
  -H 'sec-ch-ua-full-version-list: "Chromium";v="116.0.5845.42", "Not)A;Brand";v="24.0.0.0", "Microsoft Edge";v="116.0.1938.29"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-model: ""' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-ch-ua-platform-version: "15.0.0"' \
  -H 'sec-fetch-dest: document' \
  -H 'sec-fetch-mode: navigate' \
  -H 'sec-fetch-site: none' \
  -H 'sec-fetch-user: ?1' \
  -H 'sec-ms-gec: B3F47AD4A283CAB374C0451C46AAFD147C6A4DACAFF6A1C13F34B2C72B024494' \
  -H 'sec-ms-gec-version: 1-116.0.1938.29' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36 Edg/116.0.0.0' \
  -H 'x-client-data: eyIxIjoiMiIsIjEwIjoiXCJTMGg3R05HOTF2aDQ1TUZSUnZ5NHN2akRmMWdlaVJKenNxNlA3aU1WbnF3PVwiIiwiMiI6IjEiLCIzIjoiMSIsIjQiOiIyMTU4ODQ5NTM4MjY4OTM5NTA3IiwiNSI6IlwiSm9GUWpPTDk3OS9MbkRRZnlCd2N1M2FsOUN3eTZTQmdaMGNYMXBtOWVMZz1cIiIsIjYiOiJiZXRhIiwiNyI6IjE4MDM4ODYyNjQzNSIsIjkiOiJkZXNrdG9wIn0=' \
  -H 'x-edge-shopping-flag: 1' \
  --compressed
```


## 鸣谢
 - 感谢 [EdgeGPT](https://github.com/acheong08/EdgeGPT) 提供的代理 API 的方法。
 - 感谢 [Vercel AI](https://github.com/vercel-labs/ai-chatbot) 提供的基础脚手架和 [ChatHub](https://github.com/chathub-dev/chathub) [go-proxy-bingai](https://github.com/adams549659584/go-proxy-bingai) 提供的部分代码。

## License

MIT © [LICENSE](https://github.com/weaigc/bingo/blob/main/LICENSE).


