---
title: "Étape 3 : Tester l’Application migrée qui utilise l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929ce2f3-94ed-4e12-b629-e229769f825a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2eaf57c08157ffb9785f591016793c4c416704bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application-that-uses-the-sql-adapter"></a>Étape 3 : Tester l’Application migrée qui utilise l’adaptateur SQL
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en effectuant une opération d’insertion sur la table Customer. Pour ce faire, vous déposez un message de demande qui est conforme au schéma généré à l’aide de la vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer l’application BizTalk à utiliser le port d’envoi WCF-Custom pour la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Créer une demande XML conforme au schéma généré par le vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. À l’aide du mappage sortant, WCF-Custom envoyer convertit de port pour le rendre conforme au schéma pour la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et l’envoie à la base de données SQL Server.  
  
    ```  
    <Insert xmlns="http://SQLInsert">  
      <sync>  
        <after>  
          <CustomerTable Name="John" />  
        </after>  
      </sync>  
    </Insert>  
    ```  
  
2.  Emplacement de réception de coller le message de demande dans le dossier qui est mappé au fichier.  
  
3.  L’orchestration consomme le message de demande et l’envoie à la base de données SQL Server. Réception de la réponse à partir de la base de données SQL Server dans le schéma qui est conforme au schéma de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. À l’aide du mappage entrant, WCF-Custom envoyer port convertit le schéma pour le vPrev [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. La réponse à partir de la base de données SQL Server est enregistrée à l’autre emplacement de fichier définie dans le cadre de l’orchestration. La réponse pour le précédent message de demande est la suivante :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <InsertResponse xmlns="http://SQLInsert">  
      <Success>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">101</long>   
      </Success>  
    </InsertResponse>  
    ```  
  
     Dans la réponse précédente, « 101 » est la valeur de la colonne d’identité insérée dans la table Customer.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)