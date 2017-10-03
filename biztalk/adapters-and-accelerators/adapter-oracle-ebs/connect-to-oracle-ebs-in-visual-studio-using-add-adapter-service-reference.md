---
title: "Se connecter à Oracle E-Business Suite dans Visual Studio à l’aide du plug-in référence Ajouter adaptateur Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe4d1b7-8201-4816-ae90-020520f29714
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49eaa30c63d373ba20ae19f470405b851475d93a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-e-business-suite-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>Se connecter à Oracle E-Business Suite dans Visual Studio à l’aide du plug-in référence Ajouter adaptateur Service
Pour vous connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] dans une solution de programmation .NET, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Cette rubrique fournit des instructions sur l’utilisation de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## <a name="connecting-to-oracle-e-business-suite-using-the-add-adapter-service-reference-plug-in"></a>Connexion à Oracle E-Business Suite à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Les étapes suivantes pour vous connecter à Oracle E-Business Suite à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-connect-to-oracle-e-business-suite"></a>Pour vous connecter à Oracle E-Business Suite  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dans une solution de programmation :  
  
    1.  Créez un projet à l’aide de Visual Studio.  
  
    2.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **ajouter une référence de Service de carte**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] s’ouvre.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **oracleEBSBinding** et cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |||  
    |-|-|  
    |Utiliser|Pour effectuer cette opération|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie. L’interface utilisateur graphique est identique pour les [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
     ![Utiliser la boîte de dialogue de Service d’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/6a2b21ed-0fd2-4874-a6a6-e59a467533f8.gif "6a2b21ed-0fd2-4874-a6a6-e59a467533f8")  
  
     Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] affiche les différents nœuds contenant plusieurs opérations qui peuvent être effectuées sur Oracle E-Business Suite et de la base de données Oracle. Pour plus d’informations sur la façon dont les métadonnées sont classée sous différents nœuds, consultez [se connecter à Oracle E-Business Suite dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)   
 [Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)