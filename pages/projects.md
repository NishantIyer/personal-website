---
title: Projects - Nishant Iyer
display: Projects
description: List of projects I've made
plum: false
wrapperClass: 'text-center'
projects:
  Current Focus:
    - name: 'Portena'
      link: 'https://github.com/portenacode'
      desc: 'An aspiring remote desktop architecture startup'
  Cloud:
    - name: 'NoVNC Ubuntu Persistent on GCP'
      link: 'https://github.com/NishantIyer/ubuntu-xfce-web-'
      desc: "Ubuntu on the web"
    - name: 'Aliyun Terraform'
      link: 'https://github.com/NishantIyer/aliyunterraform'
      desc: "Terraform module for creating AnalyticDB for PostgreSQL on Alibaba Cloud."
    - name: 'Alibaba CFC Blockchain Application'
      link: 'https://github.com/NishantIyer/Aliyun-FC-Blockchain'
      desc: "Blockchain Application on Alibaba Cloud Function Compute"
    - name: 'Aliyun ECS Plugin'
      link: 'https://github.com/NishantIyer/aliyun-ecs-plugin'
      desc: "aliyun ecs plugin"
    - name: 'Azure Migrator to Oracle'
      link: 'https://github.com/NishantIyer/AzureMigrater'
      desc: "Migration from Azure to Oracle made hasslefree!"
    - name: 'DRATP'
      link: 'https://github.com/portenacode/DRATP'
      desc: "Dynamic Resource Allocation and Task Prioritization plugin for instances."
    - name: 'Compute-as-a-service (CoaaS)'
      link: 'https://github.com/portenacode/CoaaS'
      desc: "Compute as a service infra model just like serverless but with no cold starts and failovers."
  Web Apps:
    - name: 'Beatville'
      link: 'https://beatville.vercel.app'
      desc: "A decentralized and blazing fast privacy respecting alternative to Spotify and Youtube"
    - name: 'Nix'
      link: 'https://nixeu.nishant-26.repl.co'
      desc: "An advanced privacy-centric search engine made by me"
    - name: 'Multiplayer Chess'
      link: 'https://full-fledged-chess-web-app.nishant2609.repl.co'
      desc: "A full fledged chess app with chat functionality."
    - name: 'Cicada'
      link: 'https://cicada.nishant2609.repl.co'
      desc: "An advanced game where there's a line and you hit the balls with it removing all the anger you have on your husband"
    - name: 'Chess AI'
      link: 'https://can-you-beat-my-chess-algorithm.nishant2609.repl.co'
      desc: "Hope you beat my chess algorithm i made using minimax"
    - name: 'Notepad'
      link: 'https://notepad-1.nishant2609.repl.co'
      desc: "A rich text editor with great functionailty yet minimal layout"
  Bots/NLP/Transformers:
    - name: 'Proxima'
      link: 'https://discord.com/api/oauth2/authorize?client_id=947363163081412681&permissions=8&scope=bot'
      desc: "A 1000+ command discord bot, quite advanced and has everything you can imagine. Sadly, it never gained traction but was quite a hit among my friends"
    - name: 'Hymn'
      link: 'https://discord.com/api/oauth2/authorize?client_id=945667542997954590&permissions=8&scope=bot'
      desc: "A music playing bot :)"
    - name: 'Proxie'
      link: 'https://github.com/NishantIyer/proxie'
      desc: "A transformer/nueral model based voice assistant."
  Networking:
    - name: 'Portcom'
      link: 'https://github.com/portenacode/Portcom'
      desc: "An innovative remote connection protocol tailored for portena"
    - name: 'ESPFA'
      link: 'https://github.com/NishantIyer/espfa'
      desc: "ESP32 Port Forwarding Accelerator"
---

<!-- @layout-full-width -->

<ListProjects :projects="frontmatter.projects" />
