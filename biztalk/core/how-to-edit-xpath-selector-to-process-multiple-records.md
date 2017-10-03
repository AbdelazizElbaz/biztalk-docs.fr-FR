---
title: "Comment modifier le sélecteur XPath pour traiter plusieurs enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, editing multiple records
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: ef7e1f8d-2e29-4cef-b558-0090648bffc0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34c9b45e3fce9f4ad5730d7f03d2a568b3701742
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-xpath-selector-to-process-multiple-records"></a>Modification du sélecteur XPath pour traiter plusieurs enregistrements
Enfant distincte TypedXmlDocuments sont créés lorsqu’un TypedXmlDocument est déclaré dans le moteur ; consultez [Assert](../core/assert.md). Le moteur détermine quels TypedXmlDocuments enfants créer en fonction des sélecteurs XPath définis dans les règles. Lorsque vous créez des règles dans l’Éditeur de règles d’entreprise, la valeur du sélecteur XPath est définie par défaut sur le nœud situé au-dessus du nœud sélectionné dans l’onglet Schémas XML de l’Explorateur de faits. La valeur par défaut du champ XPath est définie sur le nœud sélectionné, par rapport à son nœud parent.  
  
 Vous pouvez, dans certains cas, souhaiter personnaliser la valeur XPath par défaut créée par l’Éditeur de règles d’entreprise lors de la création de règles. Envisageons l’exemple de document XML suivant.  
  
```  
<Order>  
   <Orderline>  
      <Hat style="Baseball">                        
         <Cost>10</Cost>  
      </Hat>  
      <Shirt color="Black">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
   <Orderline>  
      <Hat style="Bowler">                        
         <Cost>20</Cost>  
      </Hat>  
      <Shirt color="Red">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
</Order>  
```  
  
 Supposons que vous vouliez créer une règle qui calcule la valeur Total de chaque Orderline. Votre règle se présenterait alors comme suit :  
  
 IF 1==1  
  
 PUIS **/Order/Orderline/**Total = (**/Order/Orderline/Hat/**coût + **/Order/Orderline/Shirt/**coût)  
  
 La partie en gras des XPath indique la partie Sélecteur et le reste représente le XPath du champ. Il s’agit des valeurs par défaut créées par l'Éditeur. L’exécution de cette stratégie aboutirait toutefois à la création de 6 objets : 2 objets Orderline, 2 objets Hat et 2 objets Shirt. Les totaux de Orderline seraient calculés pour chaque combinaison d'objets Hat et Shirt et ils auraient toujours la même valeur, qui serait le résultat de la dernière exécution de la règle. La règle serait déclenchée 8 fois. Ce n’est pas ce qui est prévu dans ce scénario.  
  
 Une solution consisterait à modifier les valeurs XPath de la manière suivante.  
  
 IF 1==1  
  
 PUIS **/Order/Orderline/**Total = (**/Order/Orderline/**Hat/coût + **/Order/Orderline/**Shirt/coût)  
  
 Les valeurs du Sélecteur XPath des trois champs ont été définies sur la même valeur /Order/Orderline et les valeurs XPath du champ ont été modifiées en conséquence. Cela est possible en modifiant les valeurs Sélecteur XPath et Champ XPath dans la fenêtre Propriétés lorsqu'un nœud est sélectionné sous l'onglet Schémas XML. Il convient de procéder à cette modification avant de déplacer le champ dans un argument de règle.  
  
 L’exécution de la stratégie avec cette modification aboutirait au calcul correct de la valeur Total pour chaque Orderline en fonction des valeurs Cost des nœuds Hat et Shirt appartenant à cet Orderline.