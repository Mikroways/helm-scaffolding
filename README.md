The main goal to this repository is to have a library of helm scaffoldings to use
with the `helm create` command in order to:

- Automatize chart creation with some of the
  [helm best practices](https://helm.sh/docs/chart_best_practices/) and 
  [helm tips and tricks](https://helm.sh/docs/howto/charts_tips_and_tricks/)
- Act as a baseline to chart development flow.

## How to use it

In order to use this scaffoldings you just need to clone this repository and
pass along the scaffold path to the `helm create` command. I.E:

```sh
# Clone the repo
git clone git@github.com:Mikroways/helm-scaffolding.git /tmp/helm-scaffolding
# Create the chart
helm create testing-starter -p /tmp/helm-scaffolding/mw-starter
```

Althougth this method is good for just testing purposes maybe you will want to
integrate it with your existing installation.

### Integrating this scaffold with Helm

First of all it worth mentioning that Helm looks for a particular directory when
using scaffolds. That is `$HELM_HOME/starters`; usually set as 
`~/.helm/starters`.

> If you cannot find that directory or helm just ignores it; you can
> run `helm create not-important -p unexistent` and check out the path in the
> error. ;)

Having that in mind, integration with your helm installation is fair simple.
Just clone this repository in the helm search path and start using it.

```sh
# Assuming helm's search path is ~/.helm
git clone git@github.com:Mikroways/helm-scaffolding.git ~/.helm/starters/helm-scaffolding
# Start using it
helm create testing-scaffold -p helm-scaffolding/<scaffold_you_want>
```
