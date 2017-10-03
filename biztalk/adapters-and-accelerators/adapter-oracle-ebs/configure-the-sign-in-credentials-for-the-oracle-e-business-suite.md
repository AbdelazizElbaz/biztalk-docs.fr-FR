---
title: "Configurer les informations d’identification de connexion d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743ced51-706b-4788-b5a8-e0ed8ffb3b48
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acbfc92f962982292b8db73ff225dbe6699a16f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-e-business-suite"></a>Configurer les informations d’identification de connexion d’Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]demande que les clients de l’adaptateur fournir des informations d’identification du client. L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur avec Oracle E-Business Suite et d’établir une connexion.  
  
 Les clients de l’adaptateur peuvent fournir au client les informations d’identification lors de l’utilisation [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Lorsque vous utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], informations d’identification sont requises pour générer des métadonnées. Lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, les informations d’identification sont requises pour effectuer des opérations sur Oracle E-Business Suite.  
  
> [!IMPORTANT]
>  Vous pouvez spécifier les informations d’identification pour Oracle E-Business Suite ou de la base de données Oracle. Pour vous connecter et de générer des métadonnées, vous pouvez spécifier les informations d’identification. Toutefois, lors d’une opération pour appeler un artefact d’Oracle E-Business Suite, vous devez spécifier les informations d’identification Oracle E-Business Suite car ils sont requis pour définir le contexte de l’application pour l’application Oracle E-Business Suite, que vous souhaitez appeler. Pour plus d’informations sur le contexte des applications de paramètre, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 Cette section fournit des informations sur la spécification des informations d’identification du client dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="specifying-credentials-from-visual-studio"></a>Spécification des informations d’identification à partir de Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a>Pour spécifier les informations d’identification à l’aide de complément Consume Adapter Service  
  
1.  Avec le bouton droit de votre projet BizTalk, puis **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur** et Spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a>Pour spécifier les informations d’identification à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], sélectionnez **WCF-OracleEBS**. Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-OracleEBS configuré dans BizTalk Server, sélectionnez le port dans la liste des ports.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur** et Spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
8.  Cliquez sur **OK**.  
  
## <a name="specifying-credentials-from-the-biztalk-server-administration-console"></a>Spécification des informations d’identification à partir de la Console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier les informations d’identification dans le cadre de la configuration du port WCF-Custom ou WCF-OracleEBS.  
  
#### <a name="to-specify-credentials-for-the-wcf-custom-port"></a>Pour spécifier les informations d’identification pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleEBSBinding**.  
  
5.  Si vous créez un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
6.  Si vous créez un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
7.  Cliquez sur **OK**.  
  
#### <a name="to-specify-credentials-for-the-wcf-oracleebs-port"></a>Pour spécifier les informations d’identification pour le port WCF-OracleEBS  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-OracleEBS**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du port, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleEBSBinding**.  
  
6.  Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
7.  Si vous créez un port de réception dans la boîte de dialogue des propriétés de transport, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [Connexion à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)