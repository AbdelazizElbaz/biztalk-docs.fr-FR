---
title: "Se connecter à Oracle E-Business Suite dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fadc722-0098-457e-a2e2-3e9cc96eab5e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5950b9ea6a0f5fc9856720202059cf1fd058a251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-e-business-suite-in-visual-studio-using-add-adapter-metadata-wizard"></a>Se connecter à Oracle E-Business Suite dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est également exposé comme un adaptateur BizTalk et, par conséquent, vous pouvez utiliser la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les opérations que vous souhaitez effectuer sur Oracle E-Business Suite à l’aide de l’adaptateur.  
  
## <a name="connecting-to-oracle-e-business-suite-using-the-add-adapter-metadata-wizard"></a>Connexion à Oracle E-Business Suite à l’aide de l’Assistant Ajout d’adaptateur métadonnées  
 Les étapes suivantes pour vous connecter à Oracle E-Business Suite à l’aide du [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-connect-to-oracle-e-business-suite"></a>Pour vous connecter à Oracle E-Business Suite  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dans une solution BizTalk :  
  
    1.  Créez un projet BizTalk à l’aide de Visual Studio.  
  
    2.  Cliquez sur le projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
    3.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
        |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
    4.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
    5.  Dans le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], sélectionnez **WCF-OracleEBS**. Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.  
  
        > [!IMPORTANT]
        >  Si vous disposez déjà d’un port WCF-OracleEBS configuré dans BizTalk Server, sélectionnez le port à partir de la **Port** liste.  
  
    6.  Cliquez sur **Suivant**.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **oracleEBSBinding** et cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |||  
    |-|-|  
    |Utiliser|Pour effectuer cette opération|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)).  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous générez des métadonnées à l’aide [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] et que vous avez sélectionné un port d’envoi WCF-OracleEBS existant, vous pas besoin de spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie.  
  
     ![Utiliser la boîte de dialogue de Service d’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/6a2b21ed-0fd2-4874-a6a6-e59a467533f8.gif "6a2b21ed-0fd2-4874-a6a6-e59a467533f8")  
  
     Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] affiche les différents nœuds contenant plusieurs opérations qui peuvent être effectuées sur Oracle E-Business Suite et de la base de données Oracle. Pour plus d’informations sur la façon dont les métadonnées sont classée sous différents nœuds, consultez [se connecter à Oracle E-Business Suite dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)   
 [Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)