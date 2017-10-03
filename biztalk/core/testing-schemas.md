---
title: "Test de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e28b7c-9d0c-4336-8bee-4599d41a57f4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20879925ff98d5c5d6ca7d0c9ebcf11853239bba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-schemas"></a>Test de schémas
Après avoir créé un schéma, vous pourrez souhaiter valider le fait qu'il décrit la structure XML comme vous l'attendez de lui. Vous pouvez soumettre votre schéma aux trois opérations suivantes pour le valider :  
  
-   **Génération d’instance**. cette opération génère un message d'instance à partir d'un schéma, créant des données de test pour accompagner les attributs et éléments XML spécifiés par le schéma.  
  
-   **Validation de schéma**. cette opération valide la cohérence interne d'un schéma, garantissant qu'il est conforme à la norme de schéma XSD (XML Schema Definition).  
  
-   **Validation d’instance**. cette opération valide un message d'instance donné en fonction d'un schéma.  
  
 Ces trois opérations sont utiles pour tester vos schémas avant de les mettre en pratique dans un environnement de production.  
  
 Cette section décrit ces opérations de façon plus détaillée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment valider des schémas dans Visual Studio](../core/how-to-validate-schemas-in-visual-studio.md)  
  
-   [Comment valider les Messages d’Instance](../core/how-to-validate-instance-messages.md)  
  
-   [Comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md)