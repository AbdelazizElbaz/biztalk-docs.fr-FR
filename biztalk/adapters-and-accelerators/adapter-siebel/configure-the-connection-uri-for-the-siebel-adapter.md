---
title: "Configurer l’URI de connexion pour l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connection URI, specifying
ms.assetid: b89b60e9-0f3b-4305-865e-9d3b40d04648
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8017e5ccd2c033f26b03fe7443245d2fb88be960
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-connection-uri-for-the-siebel-adapter"></a>Configurer l’URI de connexion pour l’adaptateur Siebel
Une connexion URI est une chaîne de connexion pour se connecter à un système Siebel. L’URI de connexion contient différents paramètres nécessaires pour établir la connexion avec un système Siebel. Vous devez spécifier cet URI à la fois au moment du design et le moment de l’exécution de la connexion. Au moment du design, vous devez spécifier l’URI pour se connecter au système Siebel pour générer des métadonnées. Au moment de l’exécution, vous devez spécifier l’URI pour se connecter au système Siebel pour effectuer des opérations.  
  
## <a name="enter-the-connection-uri-at-design-time"></a>Entrez l’URI de connexion au moment du design  
 Pour le moment du design, vous devez spécifier l’URI de connexion à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="enter-the-connection-uri-using-consume-adapter-service-add-in"></a>Entrez l’URI à l’aide de complément Consume Adapter Service de connexion  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **siebelBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet. À partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.  
  
6.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés URI** onglet et spécifier les valeurs des paramètres différents. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les valeurs de liaison, si elle existe, qui sont nécessaires pour être spécifié avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
8.  Cliquez sur **OK**.  
  
#### <a name="enter-the-connection-uri-using-add-adapter-metadata-wizard"></a>Entrez l’URI à l’aide d’Assistant de connexion  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF-Siebel**. Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-Siebel configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **siebelBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet. À partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.  
  
8.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés URI** onglet et spécifier les valeurs des paramètres différents. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
9. Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les valeurs de liaison, si elle existe, qui sont nécessaires pour être spécifié avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un port d’envoi WCF-Siebel existant, vous ne devez pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
10. Cliquez sur **OK**.  
  
## <a name="enter-the-connection-uri-at-run-time"></a>Entrez l’URI de connexion en cours d’exécution  
 Temps d’exécution, vous devez spécifier l’URI dans le cadre de la configuration du port WCF-Custom ou WCF-Siebel dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
#### <a name="enter-the-connection-uri-for-the-wcf-custom-port"></a>Entrez l’URI de connexion pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **adresse (URI)** zone de texte, spécifiez l’URI de connexion pour se connecter au système Siebel. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
6.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **siebelBinding**.  
  
7.  Pour créer un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :  
  
    1.  Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.  
  
    2.  Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.  
  
8.  Cliquez sur **OK**.  
  
#### <a name="enter-the-connection-uri-for-the-wcf-siebel-port"></a>Entrez l’URI de connexion pour le port WCF-Siebel  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-Siebel que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.  
  
6.  Cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
7.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
8.  Pour créer un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :  
  
    1.  Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.  
  
    2.  Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)