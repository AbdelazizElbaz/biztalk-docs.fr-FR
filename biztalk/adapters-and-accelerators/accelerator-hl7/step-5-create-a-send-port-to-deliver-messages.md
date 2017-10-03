---
title: "Étape 5 : Créer un Port d’envoi pour remettre des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f56ad7a7-5c77-4191-a001-691e5e0652a1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e85033256f7a49ed506fea00a7b48db67b0da1b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-send-port-to-deliver-messages"></a>Étape 5 : Créer un Port d’envoi pour remettre des Messages
Dans cette étape, vous créez et configurez un port d’envoi des messages individuels contenus dans le lot reçu. Plus loin dans ce didacticiel, vous allez activer la fragmentation de la partie d’origine (Tutorial_BatchSource) dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration. Par conséquent, le moteur d’intégration BizTalk sera fragmenter le lot en messages individuels, et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] enverra les messages sur le port d’envoi que vous créez dans cette étape.  
  
 Vous créez ce port pour être statiques, afin qu’elle sera associé à un adaptateur MLLP, et elle n’envoie vers une destination spécifique (application métier de destination). Dans ce didacticiel, cette destination est MESA_IS, figurant dans MSH5 des messages individuels. Vous créez le port avec des filtres qui limitent le port pour envoyer des messages, pas accusés de réception, en filtrant les messages conformes au schéma ACK_024_GLO_DEF ou un accusé de réception (ACK) statique.  
  
 Configurer ce port d’envoi à recevoir les accusés de réception à partir de la destination, en associant le port d’envoi avec un port de réception nommé **TwoWayAckReceivePort**. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]le programme d’installation crée ce port et d’accompagnement l’emplacement de réception **TwoWayAckReceiveLocation**. Vous configurer le port d’envoi à utiliser avec ce port en définissant **avec sollicitation-réponse activer la** à **Oui** et en définissant le **soumettre les URI d’emplacement de réception** à  **127.0.0.1:65535** (les paramètres requis pour accepter les accusés de réception). Pour plus d’informations, consultez [paramètre d’un Port d’envoi pour recevoir les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).  
  
### <a name="to-create-a-send-port-to-deliver-messages"></a>Pour créer un port d’envoi pour remettre des messages  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_2wayMsg**.|  
    |**Type de transport**|Sélectionnez **MLLP** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir la boîte de dialogue Propriétés du Transport MLLP.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport MLLP, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de la connexion**|Type **2wayMsg**.|  
    |**Hôte**|Type **localhost**.|  
    |**Port**|Type **41000**.|  
    |**Sollicitation-réponse activé**|Cliquez sur le champ situé à droite de **activée de réponse de sollicitation**, puis sélectionnez **Oui** dans la liste déroulante.|  
    |**Soumettre emplacement de réception (URI) pour l’accusé de réception**|Type**127.0.0.1:65535**|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété** (première ligne)|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez **! =** dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété** (deuxième ligne)|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez **! =** dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété** ((troisième ligne)|Cliquez sur la deuxième ligne sous le champ **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez **! =** dans la liste déroulante.|  
    |**Valeur**|Type **StaticAck**.|  
  
7.  Cliquez sur **Entrée**. Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.  
  
8.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_2wayMsg**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 6 : créer un Port d’envoi pour remettre les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md).