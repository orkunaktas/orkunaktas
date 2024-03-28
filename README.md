<h1 align="left">Hi! im Orkun</h1>

###

<div align="left">
  <img src="https://github-readme-stats.vercel.app/api?username=orkunaktas&hide_title=false&hide_rank=false&show_icons=false&include_all_commits=true&count_private=true&disable_animations=false&theme=algolia&locale=en&hide_border=false&custom_title=GitHub%20Stats" height="163" alt="stats graph"  />
  <img src="https://streak-stats.demolab.com?user=orkunaktas&locale=en&mode=daily&theme=algolia&hide_border=false&border_radius=5" height="147.5" alt="streak graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=orkunaktas&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=6&theme=algolia&hide_border=false" height="135" alt="languages graph"  />
</div>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="43" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" height="43" alt="csharp logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/microsoftsqlserver/microsoftsqlserver-plain.svg" height="43" alt="microsoftsqlserver logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/numpy/numpy-original.svg" height="43" alt="numpy logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pandas/pandas-original.svg" height="43" alt="pandas logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/matlab/matlab-original.svg" height="43" alt="matlab logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg" height="43" alt="jupyter logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" height="43" alt="figma logo"  />
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/orkunaktas/orkunaktas/output/snake.svg" alt="Snake animation" />

###

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
