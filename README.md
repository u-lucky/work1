Workflow file for this run
.github/workflows/blank.yml at 57f7d926

1  name: CI
2  on:
3    push:
4      branches: [ "master" ]
5    workflow_dispatch:
6  jobs:
7    lint:
8      runs-on: ubuntu-latest
9      steps:
10       - uses: actions/checkout@v4
11         - name: install dependencies
12         run: npm install
13       - name: check code style
14         run: npx prettier --check ./src
15  build:
16     runs-on: ubuntu-latest
17     needs: [ lint ]
18     steps:
19       - uses: actions/checkout@v4
20       - name: Run a one-line script
21         run: echo ${{ secrets.TELEGRAM_TOKEN }}
