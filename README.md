name: Sync master to branches

on:
  push:
    branches:
      - master

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Git
        run: |
          git config --global user.email "ssaini@cloverleafanalytics.com"
          git config --global user.name "GitHub Action"

      - name: Fetch all branches
        run: git fetch --all

      - name: Merge master into branches
        run: |
          for branch in feature-1 feature-2; do
            git checkout $branch
            git merge origin/master --no-edit || true
            git push origin $branch
          done


<!---
shivaniSaini0509/shivaniSaini0509 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
