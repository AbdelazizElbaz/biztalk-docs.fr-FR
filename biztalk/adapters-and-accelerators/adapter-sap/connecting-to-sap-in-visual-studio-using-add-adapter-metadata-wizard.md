---
title: "Connexion à SAP à l’aide de Visual Studio Assistant Ajout d’adaptateur métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a442837b-e7d8-4edb-9c5e-5603d4c58fe5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db24d079dc428c69733e36141280504f97728b26
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="connecting-to-sap-in-visual-studio-using-add-adapter-metadata-wizard"></a>Connexion à SAP à l’aide de Visual Studio Assistant Ajout d’adaptateur métadonnées
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est également exposé comme un adaptateur BizTalk et par conséquent, vous pouvez utiliser la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les opérations que vous souhaitez effectuer sur un système SAP à l’aide de l’adaptateur.  
  
## <a name="connecting-to-an-sap-system-using-add-adapter-metadata-wizard"></a>Connexion à un système SAP à l’aide d’Assistant Ajout d’adaptateur métadonnées  
 Les étapes suivantes pour vous connecter à un système SAP à l’aide du [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-connect-to-an-sap-system"></a>Pour vous connecter à un système SAP  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] dans une solution BizTalk :  
  
    1.  Créez un projet BizTalk à l’aide [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
    2.  Cliquez sur le nom du projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
    3.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
        |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
    4.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
    5.  Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF SAP**. Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.  
  
        > [!IMPORTANT]
        >  Si vous disposez déjà d’un port WCF SAP configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
    6.  Cliquez sur **Suivant**.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **sapBinding** et cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP.  
  
    > [!IMPORTANT]
    >  Si vous utilisez la bibliothèque de connexions de réseau sécurisée (SNC) SAP pour se connecter à un système SAP, ne spécifiez pas un nom d’utilisateur et un mot de passe.  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
    > [!IMPORTANT]
    >  Si vous utilisez la bibliothèque SAP SNC pour se connecter à un système SAP, définissez la **UseSnc** propriété de connexion **True**.  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Par exemple, si vous souhaitez cibler une opération ReceiveIdoc, vous devez définir le **ReceiveIdocFormat** propriété de liaison de chaîne. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous générez des métadonnées à l’aide [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] et que vous avez sélectionné un port d’envoi WCF-SAP existant, vous pas besoin de spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
    > [!IMPORTANT]
    >  Si vous utilisez la bibliothèque SAP SNC pour se connecter à un système SAP, définissez la **SncLibrary** et **SncPartnerName** avec les valeurs appropriées.  
    >   
    >  Le **SncLibrary** liaison de la propriété prend le chemin d’accès et le nom du fichier DLL requis pour l’utilisation de SNC pour se connecter à un système SAP. Ces DLL doit être présent sur l’ordinateur avec le client SAP et [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installé. Pour plus d’informations, consultez la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation disponible à l’adresse \<guide d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
    >   
    >  Le **SncPartnerName** liaison de la propriété prend le nom SNC du partenaire de communication.  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie. L’interface utilisateur graphique est identique pour les [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
     ![Consume Adapter Service connecté de boîte de dialogue](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")  
  
     Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] affiche les différents nœuds contenant différents artefacts pouvant être appelées dans un système SAP. Par exemple, le **RFC** nœud contient tous les documents RFC disponibles dans le système SAP vous connecté à. Pour plus d’informations sur ces nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)