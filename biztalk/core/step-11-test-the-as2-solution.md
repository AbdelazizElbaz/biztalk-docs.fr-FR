---
title: "Étape 11 : Tester la Solution AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 184ed8ee-6778-4bb9-b265-a94a1fed03cb
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 490833859717ec37e0cb53ae89497aa361adda6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-11-test-the-as2-solution"></a>Étape 11 : Tester la Solution AS2
![Étape 11 sur 11](../core/media/tut-step11-of-11.gif "Tut_Step11_of_11")  
  
 Cette étape permet de vérifier les résultats du didacticiel.  
  
 Vous devez créer le fichier Sender.exe utilisé pour envoyer un message EDI à l'emplacement de réception Receive_AS2 (via le répertoire virtuel Contoso). Sender.exe renvoie un message MDN asynchrone. Le fichier de message (X12_00401_864.edi) est situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-test-the-solution-with-an-asynchronous-edi-message"></a>Pour tester la solution avec un message EDI asynchrone  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet Sender.csproj dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender. Cliquez sur le projet Sender, puis cliquez sur **propriétés**. Cliquez sur **signature** dans la console de gauche. Vérifiez que **signer l’assembly** est sélectionné et définir le fichier de clé de nom fort **Sender.snk**. Assurez-vous que **temporiser la signature uniquement** est désactivée.  
  
2.  créer le projet ;  
  
3.  Ouvrez une invite de commandes, puis accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug. Entrée `Sender.exe`, puis appuyez sur **entrée**. Si un message indique que le message AS2 a été correctement envoyé, vous pouvez fermer l'invite de commandes.  
  
    > [!NOTE]
    >  Sender.exe builds en cours d’exécution un message AS2 contenant les éléments suivants échange de test EDI : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\X12_00401_864.edi. Une fois le message AS2 créé, celui-ci est publié dans le répertoire virtuel Contoso qui utilise BTSHttpReceive.dll pour acheminer le message à l'emplacement de réception.  
  
4.  Accédez à la [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\dossier _MDNToFabrikam. Vérifiez qu’il existe un \<GUID > .msg des fichiers dans le dossier. Ouvrez le fichier dans le Bloc-notes et vérifiez que le message est un MDN avec l'en-tête AS2-From défini sur Contoso et l'en-tête AS2-To défini sur Fabrikam.  
  
5.  Accédez à la [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso dossier. Vérifiez qu’il existe un \<GUID > fichier .xml dans le dossier. Double cliquez sur le fichier et vérifiez que le champ ST01 du message est défini sur 864.  
  
6.  Accédez à la [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam dossier. Vérifiez qu’il existe un \<GUID > .msg des fichiers dans le dossier. Ouvrez le fichier dans le Bloc-notes et vérifiez que le message est un message 997 (avec un ST1 de 997) avec des en-têtes AS2 via une charge EDI. Vérifiez que l'en-tête AS2-From est défini sur Contoso et que l'en-tête AS2-To est défini sur Fabrikam. Vérifiez qu'ISA6 (Identificateur de l'expéditeur) est défini sur 1234567 (Contoso) et qu'ISA8 (Identificateur du récepteur) est défini sur 7654321 (Fabrikam).  
  
7.  Pour afficher les rapports d’état AS2 et EDI, accédez à la **Hub du groupe** page dans la Console Administration de BizTalk Server, faites défiler vers le bas de la page, puis cliquez sur un des liens du rapport d’état. Pour plus d’informations, consultez [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel AS2.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)   
 [Étape 1 : Préparer le didacticiel AS2](../core/step-1-prepare-for-the-as2-tutorial.md)