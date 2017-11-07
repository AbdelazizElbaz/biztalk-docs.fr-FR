---
title: "Dépanner l’adaptateur JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5a55e52-039a-4aea-8251-b697fd061ddc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eac716a7567930509ebfd310cdaf9874286b349c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-the-adapter"></a>Dépannage de l’adaptateur
Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne.  
  
## <a name="cannot-use-wildcards-in-send-port-properties"></a>Impossible d’utiliser des caractères génériques dans les propriétés du port d’envoi  
 L'adaptateur pour JD Edwards EnterpriseOne ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés de port d'envoi suivants :  
  
-   Utilisateur  
  
-   Environnement JDE  
  
-   Hôte  
  
-   Port  
  
-   Java_Home  
  
-   Fichiers JAR JDE  
  
-   Nom du serveur de sécurité  
  
-   Connexion Nom de service  
  
-   Nom de la source de données  
  
-   Propriétaire de la base de données  
  
-   Nom du serveur de base de données  
  
-   Type de base de données  
  
-   Nom de la base de données physique  
  
## <a name="connecting-to-oracle-database"></a>Connexion à la base de données Oracle  
 Lorsque vous utilisez une base de données Oracle avec JD Edwards, vous devez modifier le fichier jdeinterop.ini. À l'aide de l'authentification unique, la section [JDBj-ORACLE] définit l'emplacement Oracle tnsnames. Le paramètre de base de données doit être utilisé, et le fichier SQLNET.ORA doit être présent sur l'ordinateur BizTalk Server (inclus avec le client Oracle).  
  
 Ajoutez le code suivant au fichier jdeinterop.ini :  
  
1.  Sous [JDBj-ORACLE] :  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  Sous [JDBj-BOOTSTRAP données SOURCE] :  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter l’adaptateur et créer les artefacts](../core/adding-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [Résolution des problèmes de JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)