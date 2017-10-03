---
title: "Étape 6 : Créer un Port d’envoi pour remettre les accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 739b3e60-db56-46e9-a6b1-0acbe0c08f55
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 978ccb9bf01fe71c3ccce7315e0286ee862bb7ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-acknowledgments"></a>Étape 6 : Créer un Port d’envoi pour remettre les accusés de réception
Dans cette étape, vous créez un port pour envoyer des accusés de réception dans la source du lot.  
  
 Vous créez ce port pour être statiques, afin qu’elle sera associé à un adaptateur MLLP, et elle n’envoie vers une destination spécifique (la source du lot). Dans ce didacticiel, la source est associée au tiers Tutorial_BatchSource. Cette partie de la source est contenue dans MSH3 des messages individuels et FHS3 et BHS3 du lot d’origine.  
  
 Vous créez le port avec des filtres qui limitent le port à l’envoi d’accusés de réception, pas les messages de données. Ces filtres spécifient un type de message de ACK_024_GLO_DEF et la destination Tutorial_BatchSource.  
  
 Configurer ce port d’envoi pour les accusés de réception à partir de la destination, en associant le port d’envoi avec un port de réception nommé **TwoWayAckReceivePort**. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]le programme d’installation crée ce port et d’accompagnement l’emplacement de réception **TwoWayAckReceiveLocation**. Vous configurer le port d’envoi à utiliser avec ce port en définissant **avec sollicitation-réponse activer la** à **non** et en définissant le **soumettre les URI d’emplacement de réception** à  **127.0.0.1:65535** (les paramètres requis pour accepter les accusés de réception). Pour plus d’informations, consultez [paramètre d’un Port d’envoi pour recevoir les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).  
  
### <a name="to-create-a-send-port-to-deliver-acknowledgments"></a>Pour créer un port d’envoi pour remettre les accusés de réception  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_2wayAck**.|  
    |**Type de transport**|Sélectionnez **MLLP** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir le **propriétés du Transport MLLP** boîte de dialogue.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport MLLP, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la connexion**|Type **2wayAck**.|  
    |**Hôte**|Type **localhost**.|  
    |**Port**|Type **41002**.|  
    |**Sollicitation-réponse activé**|Conserver le champ en tant que **non**.|  
    |**Soumettre emplacement de réception (URI) pour l’accusé de réception**|Type **127.0.0.1:65535**|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    > [!NOTE]
    >  Assurez-vous que vous entrez les données suivantes exactement comme indiqué. Ces données respecte la casse.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété** (première ligne)|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **ou** dans la liste déroulante.|  
    |**Propriété** (deuxième ligne)|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété** ((troisième ligne)|Cliquez sur la deuxième ligne sous le champ **propriété**, puis sélectionnez **BTAHL7Schemas.MSH5_1**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **Tutorial_BatchSource**.|  
  
    > [!NOTE]
    >  Le premier filtre signifie que vous êtes abonné au message d’accusé de réception. Le deuxième filtre signifie que vous souhaitez que l’accusé de réception qui possède la destination du serveur de publication, **Tutorial_BatchSource**.  
  
7.  Cliquez sur **Entrée**. Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.  
  
8.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_2wayAck**, puis sélectionnez **Démarrer**.  
  
    > [!NOTE]
    >  Pour le Tutorial_2wayAck port d’envoi pour fonctionner correctement, vous devez activer la TwoWayAckReceivePort emplacement de réception.  
  
9. Cliquez sur **les emplacements de réception**. Vérifiez que l’état de la TwoWayAckReceiveLocation est activée. Avec le bouton droit dans le cas contraire, **TwoWayAckReceiveLocation**, puis cliquez sur **activer**.  
  
 Passez à [étape 7 : créer et configurer un tiers Source](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md).