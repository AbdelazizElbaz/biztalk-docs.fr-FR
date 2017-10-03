---
title: "Étape 7 : Configurer le Port d’envoi MDN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 983033ac-9d32-47c8-9bb8-b4161bcdf183
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0f70df6846553e2d64711f33e8c5a0b0e4d2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-configure-the-mdn-send-port"></a>Étape 7 : Configurer le Port d’envoi MDN
![Étape 7 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")  
  
 Dans cette étape, vous définissez un port d’envoi dynamique pour envoyer un MDN asynchrone à le \\dossier _MDNToFabrikam. Ce port d'envoi fait appel au pipeline d'envoi AS2Send pour générer la réponse MDN sortante. Dans la mesure où il s’agit d’un port d’envoi dynamique, il utilisera l’adresse dans la ligne Receipt-Delivery-Option dans l’en-tête du message pour router le message vers le \\dossier _MDNToFabrikam. Cette adresse pointe vers le répertoire virtuel Fabrikam. Le fichier Default.aspx.cs associé à ce répertoire virtuel permet de créer le MDN avec une extension .msg, puis de l'envoyer dans le dossier de destination (lequel est également spécifié à la ligne Receipt-Delivery-Option).  
  
> [!NOTE]
>  Vous pouvez également configurer l'accord de manière à envoyer le MDN à une autre adresse en remplaçant les paramètres du message par ceux de l'accord. Pour plus d'informations, consultez  
  
 Dans cet exemple, le MDN est envoyé à l'aide d'un port d'envoi dynamique ; vous pouvez toutefois utiliser un port d'envoi statique afin d'envoyer le MDN à une adresse statique. Pour plus d’informations, consultez [configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) et [configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-the-sendasyncmdn-send-port"></a>Pour créer le port d'envoi Send_Async_MDN  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **dynamique Port d’envoi unidirectionnel**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue, nommez le port d’envoi **Send_Async_MDN**.  
  
3.  Sélectionnez **AS2Send** pour **pipeline d’envoi**.  
  
    > [!NOTE]
    >  Le pipeline AS2Send est utilisé, car aucun traitement EDI n'est requis pour le MDN.  
  
4.  Cliquez sur **filtres** dans l’arborescence de la console. Dans le volet filtres, sélectionnez **EdiIntAS.IsAS2AsynchronousMdn** pour **propriété**,  **==**  pour **opérateur**, entrez **True** pour **valeur**.  
  
    > [!NOTE]
    >  Ce filtre garantit que le port d'envoi dynamique récupère uniquement les MDN asynchrones dans MessageBox.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Send_Async_MDN**, puis cliquez sur **Démarrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer le port d’envoi (**Send_Async_997**) pour envoyer le 997 accusé de réception vers Fabrikam, comme décrit dans [étape 8 : configurer le Port d’envoi 997](../core/step-8-configure-the-997-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)   
 [Configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)   
 [Configuration d’un Port d’envoi dynamique pour les Messages via AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)