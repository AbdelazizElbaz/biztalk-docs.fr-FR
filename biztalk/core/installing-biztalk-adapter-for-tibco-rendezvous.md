---
title: "Installation, les schémas et les limitations de l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Installation, de génération de schéma et les limitations de l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6404e7e-f671-4c57-a222-0bbe7cbc334f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a158d4f627a553a87f0bc8fa08333a5864bb884
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="install-schemas-and-limitations-of-the-tibco-rendezvous-adapter"></a>Installation, les schémas et les limitations de l’adaptateur TIBCO Rendezvous

## <a name="install-and-setup"></a>Installer et configurer

[Installer et configurer les adaptateurs pour les applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) inclut les étapes pour installer les adaptateurs d’entreprise et inclut également des informations clées à connaître avant d’installer l’adaptateur, et après l’installation de l’adaptateur. 

## <a name="generate-schemas"></a>Générer des schémas
Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages. La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous. En raison de cette limitation, l’adaptateur ne peut pas fournir des fonctionnalités de génération de schéma.  
  
Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations. Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio. Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.  

## <a name="limitations"></a>Limitations

- L’unicité du nom du champ n’est pas garantie. Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.  
  
-   Il n'est pas possible de classer/trier les champs.  
  
-   Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés. L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.  
  
-   La connexion sécurisée aux démons n'est pas prise en charge.  
  
-   Les types de données personnalisés ne sont pas pris en charge.  
  
-   La messagerie certifiée n'est pas prise en charge du côté transmetteur.  
-   
## <a name="next-step"></a>Étape suivante

[Didacticiels : Utilisation de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)  