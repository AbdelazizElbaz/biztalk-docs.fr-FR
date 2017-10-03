---
title: "Étape 9 : Configurer le Port d’envoi EDI charge utile | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71a8a4a7-7c3e-4e33-a9c0-a6445a3cc236
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9de1dff24af11cd03cda2550dcab921aec25d585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-configure-the-edi-payload-send-port"></a>Étape 9 : Configurer le Port d’envoi EDI charge utile
![Étape 9 sur 11](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")  
  
 Dans cette étape, vous configurez un port d’envoi pour envoyer le code XML généré à partir de la charge EDI vers l’application Contoso principale, représentée par le \\_EDIXMLToContoso dossier. Ce port d'envoi utilise un pipeline d'envoi PassThruTransmit.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-the-sendpayloadedixml-send-port"></a>Pour créer le port d'envoi Send_Payload_EdiXml  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **Send_Payload_EdiXml**. Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Le type FILE est spécifié car le pipeline d'envoi n'effectue pas de traitement AS2 sur le fichier de charge. Il s'agit juste d'acheminer le fichier de charge vers un dossier local afin de pouvoir afficher le document informatisé EDI.  
  
3.  Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, recherchez et sélectionnez [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso. Laissez **nom de fichier** en tant que **%MessageID%.xml**. Cliquez sur **OK**.  
  
4.  Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.  
  
    > [!NOTE]
    >  Le pipeline d'envoi PassThruTransmit étant utilisé, le pipeline n'effectue pas de traitement EDI sur le message de charge mais est envoyé au dossier local au format XML produit par le pipeline de réception AS2EdiReceive.  
  
5.  Cliquez sur **filtres** dans l’arborescence de la console. Pour **propriété**, entrez **BTS. MessageType**. Pour **opérateur**, entrez  **==** . Pour **valeur**, entrez `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.  
  
    > [!NOTE]
    >  Ce filtre garantit que ce port d'envoi récupère uniquement les messages de charge 864 X12 dans la base de données MessageBox.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Send_Payload_EdiXml** port d’envoi, puis cliquez sur **Démarrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous créez un AS2 et X12 accord entre les deux commerciaux partenaires, comme décrit dans [étape 10 : configurer le X12 et accord de partenariat commercial AS2](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)