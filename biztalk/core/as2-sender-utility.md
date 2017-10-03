---
title: "AS2 L’utilitaire Sender | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e2a88fc-67fd-4801-a6f8-1e7c92098eaf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69f70e2a404c92393fb02b301b58abf2d97da2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-sender-utility"></a>Utilitaire Expéditeur AS2
L'utilitaire AS2 Sender inclus avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'envoyer un message AS2 vers un site Web sur un seul ordinateur. Il simule l'envoi d'un message AS2 à partir d'un ordinateur distinct.  
  
 Les fichiers de cet utilitaire sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="what-this-utility-does"></a>Fonctions de l'utilitaire  
 L'utilitaire AS2 Sender génère un message AS2 avec une charge EDI, puis envoie celui-ci vers un site Web utilisant le filtre ISAPI BTSHTTPReceive. Le didacticiel effectue les tâches suivantes par défaut :  
  
-   Envoie un message AS2 nommé X12_00401_864.edi avec une charge 864 X12. Ce message se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.  
  
-   Demande un MDN asynchrone en réponse au message AS2. Ceci est déterminé par le message envoyé et peut être modifié.  
  
-   Envoie le message AS2 vers un emplacement de réception via le répertoire virtuel Contoso.  
  
 L'utilitaire peut être modifié pour changer ce comportement spécifique. Consultez le [comment personnaliser l’utilitaire AS2 Sender](../core/as2-sender-utility.md#BKMK_Custom) section ci-dessous.  
  
## <a name="how-to-set-up-a-solution-using-the-as2-sender-utility"></a>Configuration d'une solution se servant de l'utilitaire AS2 Sender  
 Pour configurer une solution pour qu'elle fasse appel à l'utilitaire AS2 Sender, procédez comme suit :  
  
> [!IMPORTANT]
>  Ces étapes sont décrites dans le didacticiel AS2 et dans deux procédures pas à pas AS2 côté envoi. Pour plus d’informations, consultez [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md), [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md), et [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un asynchrone MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).  
  
-   Activez le filtre ISAPI BTSHTTPReceive.  
  
-   Configurez une page Web et un emplacement de réception pour recevoir le message AS2. Dans l'utilitaire AS2 Sender par défaut, la page Web est la page Web Contoso.  
  
-   Déployez le schéma de l'échange EDI que vous allez envoyer en tant que charge du message AS2.  
  
-   Définissez les propriétés de tiers AS2 et EDI appropriées.  
  
##  <a name="BKMK_Custom"></a>La personnalisation de l’utilitaire AS2 Sender  
 L'utilitaire AS2 Sender par défaut envoie un échange 864 EDI de test via AS2 vers la page Web Contoso à l'aide du filtre ISAPI BTSHTTPReceive. Le message AS2, nommé X12_00401_864.edi, demande un MDN asynchrone. Le code de l'utilitaire AS2 Sender est situé dans HttpSender.cs dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender. La ligne de code suivante dans HttpSender.cs envoie le fichier de test 864 par défaut :  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
```  
  
> [!NOTE]
>  Vous pouvez modifier cette ligne en changeant le nom et le chemin d'accès du fichier.  
  
 La ligne suivante dans HttpSender.cs envoie un message AS2 nommé X12_00401_864-Sync.EDI. Ce message demande un MDN synchrone. Par défaut, cette ligne de code dans HttpSender.cs est commentée en faveur de la ligne qui envoie X12_00401_864.edi. Pour envoyer X12_00401_864-Sync.edi, supprimez le commentaire de la ligne X12_00401_864-Sync.edi et commentez la ligne X12_00401_864.edi.  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
```  
  
 La ligne de code suivante dans HttpSender.cs envoie le message vers la page Web Contoso :  
  
```  
HttpSender TestSender = new HttpSender("http://localhost/Contoso/BTSHttpReceive.dll");  
```  
  
> [!NOTE]
>  Vous pouvez modifier cette ligne en changeant le répertoire virtuel et le filtre ISAPI.  
  
### <a name="to-build-the-as2-sender-sample"></a>Pour créer l'exemple AS2 Sender  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet Sender.csproj dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.  
  
2.  Ouvrez HttpSender.cs dans le projet Sender, puis personnalisez le code Sender en indiquant la page Web de réception, le nom de fichier EDI et le chemin d'accès appropriés.  
  
3.  Cliquez sur le projet Sender, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur **signature** dans la console de gauche. Vérifiez que **signer l’assembly** est sélectionnée, et le fichier de clé de nom fort est défini sur **Sender.snk**. Assurez-vous que **temporiser la signature uniquement** est désactivée.  
  
5.  créer le projet ;  
  
### <a name="to-run-the-as2-sender-sample"></a>Pour exécuter l'exemple AS2 Sender  
  
1.  Ouvrez une invite de commandes. Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.  
  
2.  Entrée **Sender.exe**, puis appuyez sur **entrée**.  
  
3.  Si un message indique que le message AS2 a été correctement envoyé, vous pouvez fermer l'invite de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)   
 [Procédure pas à pas (AS2) : Envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)   
 [Procédure pas à pas (AS2) : Envoi d’EDI via AS2 avec MDN asynchrone](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)