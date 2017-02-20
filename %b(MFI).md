# %b(MFI)

%b(MFI) est une normalisation de l'indicateur __Money Flow Index__ (MFI). 

## MFI

Cet indicateur est un oscillateur des prix pond�r�s par les volumes qui mesure la pression haussi�re et baissi�re. Le calcul de l'indicateur en tant que tel est pr�d�fini dans ProRealTime et pet �tre retrouv� sur [Stock Charts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:money_flow_index_mfi).

## %b sur l'indicateur MFI

_%b_ fait r�f�rence � la notation utilis�e par Bollinger dans son indicateur �ponyme (aka Bornes de Bollinger). Ainsi, on applique les [Bollinger](https://fr.wikipedia.org/wiki/Bandes_de_Bollinger) sur le MFI afin d'�valuer la volatilit� de l'indicateur MFI en vue d'analyses techniques.

Comme l'indique l'auteur dans son livre, il faut �tre prudent avec l'indicateur _%b_ et on ne cherchera pas � interpr�ter toute sortie au-del� des bandes comme un signal en tant que tel. On peut n�anmoins s'amuser � rechercher des divergences entre cet indicateur et les prix.

## Divergences sur %b(MFI)

Une divergence appara�t lorsque les prix forment des hauts ascendants alors que l'indicateur fait des hauts descendants ou lorsque les prix forment des bas descendants alors que l'indicateur fait des bas ascendants.

Une divergence sur les volumes indique (surtout dans le cadre d'une hausse des prix) que ce sont les petits porteurs qui font �voluer les cours. La hausse se fait sans � carburant �, sans support des institutionnels ou des fonds et a peu de chances de perdurer. Une divergence haussi�re sur les volumes est aussi vraie mais peut-�tre plut�t le signe de la vente panique de fin de baisse (climax) : les volumes ne sont pas aussi n�cessaires � la baisse qu'ils le sont � la hausse (cela tombe beaucoup plus vite que cela ne monte).

Une divergence sur _%b_ exprime la relativit� de l'�volution des prix par rapport aux bandes de Bollinger. Une divergence baissi�re sur _%b_ exprime le fait que les prix font des hauts absolus ascendants mais des hauts moins hauts relativement aux bandes. De m�me, une divergence haussi�re sur _%b_ exprime le fait que les prix font des plus bas absolus mais des bas moins bas relativement aux bandes. Ces moins hauts relatifs (pour une divergence baissi�re) et ces moins bas relatifs (pour une divergence haussi�re) sont annonciateurs d'un retournement de tendance sur les prix.

Une divergence sur _%b(MFI)_ permet aussi d'anticiper un retournement de tendance. En effet, un moins haut relatif sur cet indicateur indique une contradiction entre l'indicateur MFI qui baisse alors que les prix montent. De m�me, une divergence haussi�re sur _%b(MFI)_ indique que l'indicateur cro�t alors que les prix continuent de baisser : cela signifie que les prix continuent de baisser mais avec une force relative et des volumes moins marqu�s qu'au pr�c�dent plus bas ; signe que le rapport de forces entre baissiers et haussiers est en train de s'�quilibrer ou de se renverser en faveur des haussiers.

## ProRealTime

### Variables

- pMFI (P�riode MFI) : 10
- longueurBollinger (Longueur des bandes de Bollinger appliqu� � l'indicateur normalis�) : 40
- Horizontales � 0 et � 1
- plus remplissages au-dessus de 1 et en-dessous de 0

### Code

```bash
dividende=MoneyFlowIndex[pMFI] - BollingerDown[longueurBollinger](MoneyFlowIndex[pMFI])
diviseur= BollingerUp[longueurBollinger](MoneyFlowIndex[pMFI]) -  BollingerDown[longueurBollinger](MoneyFlowIndex[pMFI])

RETURN dividende / diviseur
```

