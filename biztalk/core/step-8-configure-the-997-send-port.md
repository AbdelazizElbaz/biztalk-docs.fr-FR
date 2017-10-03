---
title: "Étape 8 : Configurer le Port de 997 envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4780c491-9f1a-4f13-b346-6a2e1801ec09
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec3c022ec1236d760c69250a2faecc7cacdb543c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-997-send-port"></a>Étape 8 : Configurer le Port de 997 envoi
![Étape 8 sur 11](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")  
  
 Cette étape vous permet de configurer un port d'envoi pour envoyer le message 997 au partenaire. Ce port d'envoi utilise le pipeline d'envoi AS2EdiSend pour transporter un accusé de réception 997 EDIINT/AS2 vers le dossier _997ToFabrikam.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-the-sendasync997-send-port"></a>Pour créer le port d'envoi Send_Async_997  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique** .  
  
    > [!NOTE]
    >  Vous utilisez un port d'envoi unidirectionnel statique, car aucun MDN n'a été configuré en tant que récepteur des messages AS2 au niveau du tiers Fabrikam.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, nommez votre port d’envoi **Send_Async_997**. Sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.  
  
3.  Dans le **propriétés du Transport HTTP** boîte de dialogue, pour **URL de Destination**, entrez `http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`. Désactivez **activer le codage segmenté** puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le **URL de Destination** paramètre s’assure que le port d’envoi envoie le message 997 vers le répertoire virtuel Fabrikam. Le fichier Default.aspx.cs associé à ce répertoire virtuel permet de créer le message 997 avec une extension .msg, puis de l'envoyer dans le dossier de destination.  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue, sélectionnez **AS2EdiSend** pour **Pipeline d’envoi**.  
  
5.  Cliquez sur **filtres** dans l’arborescence de la console. Pour **propriété**, sélectionnez **BTS. MessageType**. Pour **opérateur**, sélectionnez  **==** . Pour **valeur**, entrez `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.  
  
    > [!NOTE]
    >  Ce filtre garantit que le port d'envoi récupère uniquement les accusés de réception 997 dans MessageBox.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Send_Async_997** port d’envoi, puis cliquez sur **Démarrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer le port d’envoi (**Send_Payload_EdiXml**) pour envoyer la charge EDI à Contoso, comme décrit dans [étape 9 : configurer le Port d’envoi EDI charge utile](../core/step-9-configure-the-edi-payload-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)   
 [Configuration d’un Port d’envoi statique pour les Messages via AS2](../core/configuring-a-static-send-port-for-messages-over-as2.md)