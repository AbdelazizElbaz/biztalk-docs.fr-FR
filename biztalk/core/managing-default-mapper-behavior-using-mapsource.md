---
title: "Gérer le comportement du mappeur par défaut à l’aide &lt;mapsource&gt; | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: deea839c-e52e-44c6-ac0d-4396dc5b10d8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44e2e66350709c6b857d875ec3979fe3f7059648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-default-mapper-behavior-using-ltmapsourcegt"></a>Gérer le comportement du mappeur par défaut à l’aide &lt;mapsource&gt;
Vous pouvez modifier certains comportements par défaut du Mappeur BizTalk en modifiant les attributs de la **mapsource** élément directement dans un fichier source (.btm) de mappage.  
  
## <a name="optimizing-value-mapping-functoid-code-generation"></a>Optimisation de la génération de code du fonctoid Mappage des valeurs  
 Lorsque le Mappeur génère du code XSLT pour appeler le **mappage** fonctoid, une variable est utilisée pour stocker le résultat. Que vous pouvez utiliser la **OptimizeValueMapping** indicateur pour optimiser la **mappage des valeurs** fonctoid afin que la variable est générée uniquement lorsque le `if` instruction prend la valeur `True`. Par exemple, avec **OptimizeValueMapping** la valeur **non**:  
  
```  
<xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 Ce code peut être optimisé en déplaçant le **mappage des valeurs** appel du fonctoid dans le corps de la `if` instruction, garantissant qu’appel produit uniquement lorsqu’il est requis. Paramètre **OptimizeValueMapping** à **Oui** génère le code suivant :  
  
```  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 Le Mappeur effectue cette optimisation automatiquement si vous définissez la **OptimizeValueMapping** attribut de la **mapsource** élément dans le fichier source (.btm) de carte à **Oui** en tant que indiqué :  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="Yes" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
## <a name="accommodating-schemas-with-large-footprints"></a>Prise en compte des schémas de grande taille  
 Lorsque le Mappeur utilise un schéma dont la taille d'instance est très importante et qui comporte des nœuds récursifs et/ou des structures complexes profondes, le test, la validation ou la compilation du mappage peuvent durer longtemps, voire même générer une erreur de mémoire insuffisante. Ceci peut se produire dans les petits schémas complexes, ainsi que dans les schémas de grande taille.  
  
 Le problème avec des schémas complexes est dû au fait que le Mappeur a charger de manière récursive l’arborescence de l’ensemble du schéma recherche pour les nœuds qui disposent connectés à des liens ou les **valeur** jeu de propriétés. Vous pouvez résoudre ce problème en définissant le **GenerateDefaultFixedNodes** indicateur de la **mapsource** élément dans les fichiers .btm **non** comme indiqué :  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="No" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 Ainsi, le Mappeur n'a pas besoin de créer, dans le compilateur interne, des nœuds associés à chaque nœud de schéma d'un schéma cible. Seuls les nœuds liés sont pris en compte par le compilateur. Vous réduisez ainsi considérablement la consommation de mémoire et accélérez les opérations de test, de validation, de compilation ou d'enregistrement de mappage.  
  
 Toutefois, lorsque le **GenerateDefaultFixedNodes** est défini à **non**, les valeurs de champ par défaut définies dans le schéma cible ne sont pas conservés dans l’instance produite par le mappage. Ceci pose problème lorsque ces valeurs sont requises dans l'instance cible. Pour contourner ce problème, les valeurs requises doivent être à nouveau définies de façon explicite dans le mappage. Vous pouvez définir le **GenerateDefaultFixedNodes** indicateur **RequiredDefaults**, ce qui signifie que tous les requis nœuds sont pris en compte. Cette rubrique décrit les nœuds liés, les valeurs de nœuds qui ont la valeur par défaut, les nœuds avec le **MinOccurs** propriété la valeur supérieure ou égale à zéro, ainsi que les nœuds dont les parents sont requis.  
  
> [!NOTE]
>  Après avoir défini **GenerateDefaultFixedNodes** à **non** ou **RequiredDefaults**, vous devez tester le mappage et vérifiez que la sortie est la même que lorsque  **GenerateDefaultFixedNodes** est défini sur sa valeur par défaut **Oui**, dans lequel tous les nœuds sont pris en compte par le compilateur.  
  
## <a name="managing-for-each-usage-with-looping-conditional-and-value-mapping-functoids"></a>Gestion de l'utilisation for-each avec les fonctoids Bouclage, Conditionnel et Mappage des valeurs  
 Lorsque vous utilisez un **bouclage** fonctoid, un **conditionnelle** fonctoid, ou un **mappage** fonctoid, un `xsl:for-each` instruction est générée dans le mappage compilé. Si le champ enfant du schéma de destination comporte un nombre maximal d'occurrences non liées, l'instruction `xsl:for-each` est placé dans le champ enfant. Si le champ enfant ne comporte pas de nombre maximal d'occurrences non liées, l'instruction `xsl:for-each` est placée dans le champ parent de ce champ.  
  
 Toutefois, étant donné que l’emplacement de la `xsl:for-each` instruction affecte le résultat du mappage, vous souhaiterez peut-être le `xsl:for-each` instruction à placer dans le champ enfant du schéma de destination, même si le nombre maximal d’occurrences du champ enfant est défini sur **1**.  
  
 Vous pouvez contrôler le placement de la `xsl:for-each` instruction en modifiant la valeur de la **TreatElementsAsRecords** d’attribut dans le fichier de mappage (.btm) comme indiqué :  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 Lorsque cet attribut a la valeur **Oui**, le `xsl:for-each` instruction est placée dans le champ enfant du schéma de destination, même si le nombre maximal d’occurrences du champ enfant est défini sur **1**.  
  
## <a name="preserving-the-order-when-mapping-a-repeating-sequence-group"></a>Préservation de l'ordre lors du mappage d'un groupe Séquence répété  
 Les groupes Séquence des schémas XSD ne fournissent pas de contexte de bouclage car ils ne sont pas représentés dans l'instance de message. Sans possibilité de bouclage du groupe Séquence, le compilateur du Mappeur ne génère pas le fichier XSLT approprié pour conserver l'ordre des segments. Par conséquent, le contexte relatif présent dans l'instance d'entrée est perdu, ce qui rend les instances de sortie inutiles pour tout traitement ultérieur dépendant du contexte relatif.  
  
 Vous pouvez utiliser la **PreserveSequenceOrder** indicateur permettant de conserver l’ordre des enregistrement lorsque vous mappez une répétition de séquence sur une autre. Par défaut, la valeur de l’indicateur est définie **non** pour préserver les fonctionnalités des mappages existants créés dans des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions où l’indicateur n’est pas présent. Dans les cartes qui vient d’être créés, l’indicateur sera présent avec sa valeur est définie sur **non**. Pour conserver l’ordre des segments, vous devez définir explicitement la valeur **Oui** dans les fichiers .btm, comme indiqué :  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" PreserveSequenceOrder="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 Le code suivant présente un exemple d'instance d'entrée :  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
 Avec la **PreserveSequenceOrder** indicateur défini sur **non**, l’instance de sortie doit ressembler à ce qui suit :  
  
```  
<Name>Person1</Name>  
<Name>Person2</Name>  
<Gender>Male</Gender>  
<Gender>Female</Gender>  
<Address>Bellevue</Address>  
<Address>Redmond</Address>  
```  
  
 Avec la **PreserveSequenceOrder** indicateur défini sur **Oui**, l’instance de sortie doit ressembler à ce qui suit :  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)