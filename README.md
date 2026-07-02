name: Automatisk Oppdatering av README Hver 10. Dag

on:
  schedule:
    - cron: '0 0 */10 * *' # Kjør klokken 00:00 UTC hver 10. dag

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Oppdater README-fil
        run: |
          echo "Sist oppdatert: $(date)" >> README.md

      - name: Commit og push endringer
        run: |
          git config --global user.name "GitHub Actions"
          git config --global user.email "actions@github.com"
          git add README.md
          git commit -m "Automatisk oppdatering av README for å holde repositoryet aktivt"
          git push
