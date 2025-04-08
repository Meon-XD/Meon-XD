name: Update Stats
on:
  schedule:
    - cron: '0 12 * * *'
  workflow_dispatch:
  push:
    branches: [ main ]

jobs:
  update:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@v7.0.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          filename: metrics/anilist.svg
          plugin_anilist: yes
          plugin_anilist_user: YourAniListUsername
          plugin_anilist_medias: anime
          plugin_anilist_sections: favorites,watching
          plugin_anilist_limit: 5
          plugin_anilist_cover: yes
