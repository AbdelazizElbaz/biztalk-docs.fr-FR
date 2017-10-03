---
title: "Configurer l’URI de connexion pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2bb02b4-4ad6-4b07-b48a-8f9a47967ffc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cf8f0e81c7330b469070efb7457f22d1fed790d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-connection-uri-for-oracle-e-business-suite"></a>Configurer l’URI de connexion pour Oracle E-Business Suite
URI de connexion est une chaîne de connexion qui contient les paramètres requis pour se connecter à Oracle E-Business Suite. Lors de l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’URI pour se connecter à Oracle E-Business Suite pour générer des métadonnées. Lors de la configuration d’une orchestration à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier l’URI pour se connecter à Oracle E-Business Suite pour effectuer des opérations.  
  
## <a name="specifying-the-connection-uri-from-visual-studio"></a>Spécification de la connexion URI à partir de Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’URI de connexion à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-specify-the-connection-uri-using-consume-adapter-service-add-in"></a>Pour spécifier l’URI à l’aide de complément Consume Adapter Service de connexion  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet. À partir de la **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
6.  Cliquez sur le **propriétés URI** onglet et spécifier les valeurs des paramètres différents. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
7.  Cliquez sur le **propriétés de liaison** onglet et spécifiez les valeurs de liaison, si elle existe, qui sont nécessaires avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
8.  Cliquez sur **OK**.  
  
#### <a name="to-specify-the-connection-uri-using-add-adapter-metadata-wizard"></a>Pour spécifier l’URI à l’aide d’Assistant de connexion  
  
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
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet. À partir de la **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
    |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
    |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
8.  Cliquez sur le **propriétés URI** onglet et spécifier les valeurs des paramètres différents. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
9. Cliquez sur le **propriétés de liaison** onglet et spécifiez les valeurs de liaison, si elle existe, qui sont nécessaires avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un existant port d’envoi WCF-OracleEBS, vous ne spécifiez ne pas les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
10. Cliquez sur **OK**.  
  
## <a name="specifying-the-connection-uri-from-the-biztalk-server-administration-console"></a>Spécification de la connexion URI à partir de la Console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier l’URI de connexion dans le cadre de la configuration du port WCF-Custom ou WCF-OracleEBS.  
  
#### <a name="to-specify-the-connection-uri-for-the-wcf-custom-port"></a>Pour spécifier l’URI de connexion pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **adresse (URI)** zone de texte, spécifiez l’URI de connexion pour se connecter à Oracle E-Business Suite. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
6.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleEBSBinding**.  
  
7.  Si vous créez un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
8.  Si vous créez un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
9. Cliquez sur **OK**.  
  
#### <a name="to-specify-the-connection-uri-for-the-wcf-oracleebs-port"></a>Pour spécifier l’URI de connexion pour le port WCF-OracleEBS  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** liste déroulante, sélectionnez le WCF-OracleEBS carte vous ajoutez précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.  
  
6.  Cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [configurer l’URI de connexion pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  
  
7.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
    > [!NOTE]
    >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
8.  Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.  
  
9. Si vous créez un port de réception dans la boîte de dialogue des propriétés de transport, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à Oracle E-Business Suite.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Pour se connecter à l’aide des informations d’identification de la base de données Oracle**|Spécifiez le **ClientCredentialType** liaison de propriété **base de données** et spécifiez les informations d’identification de la base de données pour **nom d’utilisateur** et **mot de passe**zones de texte.|  
        |**Pour se connecter à l’aide des informations d’identification Oracle E-Business Suite**|Spécifiez le **ClientCredentialType** liaison de propriété **EBusiness** et spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe**  zones de texte. Dans ce cas, vous devez également spécifier des informations d’identification de la base de données Oracle pour **OracleUserName** et **OraclePassword** propriétés de liaison.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « Database »**|Spécifiez « / » pour le **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.|  
        |**Pour se connecter à l’aide de l’authentification Windows si ClientCredentialType a la valeur « EBusiness »**|Spécifiez les informations d’identification Oracle E-Business Suite pour **nom d’utilisateur** et **mot de passe** zones de texte. Vous devez également spécifier une « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.|  
  
    -   Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [Connexion à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)