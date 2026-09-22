
#épidémiologie 
On interroge 2 groupes de 200 sujets atteints d'une maladie déterminée et sujets témoins sur le contact qu'ils ont pu avoir dans le passé avec une substance réputée dangereuse. Les résultats sont consignés ci-dessous:

| Contact      | Témoins | Malades |  Total  |
| :----------- | :-----: | :-----: | :-----: |
| **Nul**      |   40    |   20    |   60    |
| **Rare**     |   100   |   100   |   200   |
| **Fréquent** |   60    |   80    |   140   |
| **Total**    | **200** | **200** | **400** |

> [!faq]- De quel type d'enquête s'agit-il
> **Enquête rétrospective** = **étude Cas-Témoins**

> [!faq]- Il s'agit de variables
> - La variable principale étudiée est le niveau de contact, qui s'exprime par des catégories non numériques ordonnées ("Nul", "Rare", "Fréquent"). C'est donc une **variable qualitative** (plus précisément qualitative ordinale).
> - Dans le cadre d'une étude d'observation épidémiologique (non expérimentale), le niveau d'exposition passé des sujets n'est pas manipulé par l'investigateur, les effectifs observés découlent du hasard du recrutement des malades et des témoins : ce sont des **variables aléatoires**.

> [!faq]- Le test de signification à appliquer pour tester la liaison entre le contact et la maladie est
> Un test du $Khi^{2}$ à 2 d.d.l.
>> - Pour croiser deux variables qualitatives (Statut de santé à 2 modalités : Malades / Témoins $\times$ Niveau de contact à 3 modalités : Nul / Rare / Fréquent), on utilise un tableau de contingence. Le test statistique approprié pour analyser l'indépendance ou la liaison entre ces variables est le **test du $Khi^{2}$ d'indépendance**.
>> - Le nombre de degrés de liberté ($d.d.l.$) se calcule par la formule :
>>  $$\text{d.d.l.} = (\text{nombre de lignes} - 1) \times (\text{nombre de colonnes} - 1)$$
>> $$\text{d.d.l.} = (3 - 1) \times (2 - 1) = 2 \times 1 = 2~\text{d.d.l.}$$

> [!faq]- Le test de signification adapté a permis de mettre en évidence une différence significative au risque $\alpha=1\%$. Peut-on conclure que le contact avec la substance est à l'origine de cette maladie ?
> Non, on ne peut pas conclure à un lien de cause à effet.
