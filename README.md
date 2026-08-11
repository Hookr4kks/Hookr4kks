<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Hookr4kks&show_icons=true&theme=tokyonight&hide_border=true&bg_color=171717&title_color=ffffff&text_color=c9c9c9&icon_color=8b5cf6" width="48%" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Hookr4kks
    &layout=compact&theme=tokyonight&hide_border=true&bg_color=171717&title_color=ffffff&text_color=c9c9c9" width="48%" />
</p>
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 */12 * * *"  # roda a cada 12h
  workflow_dispatch: {}
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate dark-themed snake animation
        uses: Platane/snk@v3
        with:
          github_user_name: Hookr4k
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push snake animation to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
