---
title: "Conservation des délimiteurs dans le composant de Pipeline assembleur fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adc27561-9996-49a9-b715-e313b9148506
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9d10879adfbe0ca0c68376faa48d9976fc19599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="retaining-delimiters-in-the-flat-file-assembler-pipeline-component"></a>Conservation des délimiteurs dans le composant de pipeline Assembleur de fichier plat
En cas d'enregistrements manquants dans le message acheminé via un pipeline personnalisé utilisant l'Assembleur de fichier plat, le délimiteur de ces enregistrements peut ou peut ne pas apparaître dans la sortie du fichier plat selon l'emplacement dans le fichier d'entrée où les enregistrements manquent.  
  
 Pour que le fichier plat conserve certains délimiteurs, vous pouvez utiliser un mappage et un script personnalisé afin de vous assurer qu'un enregistrement « vide » sera créé lorsqu'un enregistrement d'entrée spécifique n'existera pas dans le message. Pour que cela fonctionne, vous devez vérifier que les nœuds potentiellement vides dans le schéma de document pour l'Assembleur de fichier plat disposent des propriétés suivantes définies comme suit :  
  
|Propriété|Paramètre|  
|--------------|-------------|  
|Préserver le délimiteur pour les données vides|Oui|  
|Supprimer les délimiteurs de fin|Non|  
|Générer les nœuds vides (définissez cette propriété sur le nœud racine)|True|  
  
### <a name="to-create-a-map-that-creates-an-empty-record"></a>Pour créer un mappage qui génère un enregistrement « vide »  
  
1.  Ajoutez un nouveau mappage à votre projet BizTalk.  
  
2.  Spécifiez le schéma de document utilisé par l'Assembleur de fichier plat, à la fois en tant que source de mappage et schéma de destination du mappage.  
  
3.  Mappez les champs sources qui ne seront pas vides aux champs de destination correspondants.  
  
4.  Pour les champs qui peuvent être vides, utiliser un script personnalisé pour vérifier si le champ source est vide et retourner une chaîne vide (au lieu de Nil). Utilisez un script similaire à celui indiqué ci-après :  
  
    ```  
    public string ValOrEmpty(string val)  
    {  
         return (val.Length > 0) ? val : "";  
    }  
    ```  
  
    > [!NOTE]
    >  Vous devez créer un script avec un nom de fonction unique pour chaque champ potentiellement vide que vous mappez. Par exemple, si trois champs peuvent être vides, vous aurez les fonctions `ValOrEmpty1`, `ValOrEmpty2`, `ValOrEmpty3`.  
  
5.  À l’aide de la console d’Administration de BizTalk Server, de configurer le port d’envoi avec le pipeline personnalisé et le composant Assembleur de fichier plat à utiliser la carte en tant qu’un mappage sortant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md)