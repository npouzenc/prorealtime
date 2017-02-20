# %b(MFI)

%b(MFI) est une normalisation de l'indicateur __Money Flow Index__ (MFI). 

## MFI

Cet indicateur est un oscillateur des prix pondérés par les volumes qui mesure la pression haussière et baissière. Le calcul de l'indicateur en tant que tel est prédéfini dans ProRealTime et pet être retrouvé sur [Stock Charts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:money_flow_index_mfi).

## %b sur l'indicateur MFI

_%b_ fait référence à la notation utilisée par Bollinger dans son indicateur éponyme (aka Bornes de Bollinger). Ainsi, on applique les [Bollinger](https://fr.wikipedia.org/wiki/Bandes_de_Bollinger) sur le MFI afin d'évaluer la volatilité de l'indicateur MFI en vue d'analyses techniques.

Comme l'indique l'auteur dans son livre, il faut être prudent avec l'indicateur _%b_ et on ne cherchera pas à interpréter toute sortie au-delà des bandes comme un signal en tant que tel. On peut néanmoins s'amuser à rechercher des divergences entre cet indicateur et les prix.

## Divergences sur %b(MFI)

Une divergence apparaît lorsque les prix forment des hauts ascendants alors que l'indicateur fait des hauts descendants ou lorsque les prix forment des bas descendants alors que l'indicateur fait des bas ascendants.

Une divergence sur les volumes indique (surtout dans le cadre d'une hausse des prix) que ce sont les petits porteurs qui font évoluer les cours. La hausse se fait sans « carburant », sans support des institutionnels ou des fonds et a peu de chances de perdurer. Une divergence haussière sur les volumes est aussi vraie mais peut-être plutôt le signe de la vente panique de fin de baisse (climax) : les volumes ne sont pas aussi nécessaires à la baisse qu'ils le sont à la hausse (cela tombe beaucoup plus vite que cela ne monte).

Une divergence sur _%b_ exprime la relativité de l'évolution des prix par rapport aux bandes de Bollinger. Une divergence baissière sur _%b_ exprime le fait que les prix font des hauts absolus ascendants mais des hauts moins hauts relativement aux bandes. De même, une divergence haussière sur _%b_ exprime le fait que les prix font des plus bas absolus mais des bas moins bas relativement aux bandes. Ces moins hauts relatifs (pour une divergence baissière) et ces moins bas relatifs (pour une divergence haussière) sont annonciateurs d'un retournement de tendance sur les prix.

Une divergence sur _%b(MFI)_ permet aussi d'anticiper un retournement de tendance. En effet, un moins haut relatif sur cet indicateur indique une contradiction entre l'indicateur MFI qui baisse alors que les prix montent. De même, une divergence haussière sur _%b(MFI)_ indique que l'indicateur croît alors que les prix continuent de baisser : cela signifie que les prix continuent de baisser mais avec une force relative et des volumes moins marqués qu'au précédent plus bas ; signe que le rapport de forces entre baissiers et haussiers est en train de s'équilibrer ou de se renverser en faveur des haussiers.

## ProRealTime

### Variables

- pMFI (Période MFI) : 10
- longueurBollinger (Longueur des bandes de Bollinger appliqué à l'indicateur normalisé) : 40
- Horizontales à 0 et à 1
- plus remplissages au-dessus de 1 et en-dessous de 0

### Code

```bash
dividende=MoneyFlowIndex[pMFI] - BollingerDown[longueurBollinger](MoneyFlowIndex[pMFI])
diviseur= BollingerUp[longueurBollinger](MoneyFlowIndex[pMFI]) -  BollingerDown[longueurBollinger](MoneyFlowIndex[pMFI])

RETURN dividende / diviseur
```

