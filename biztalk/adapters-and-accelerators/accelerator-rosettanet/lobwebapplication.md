---
title: LOBWebApplication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, LOBWebApplication
- ASPX pages, LOBWebApplication utility
- virtual servers
- ASPX pages, submitting actions
- LOBWebApplication
- ASPX pages, response messages
- LOBWebApplication utility
ms.assetid: 2d578efd-72a9-4621-9274-30792bf94b6c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9be49eab2560cc9e9eab5a29456a27f92760e5d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="lobwebapplication"></a>LOBWebApplication
Vous utilisez l’utilitaire LOBWebApplication pour envoyer un message d’action ou d’une réponse à partir d’une page ASPX à un partenaire commercial, en simulant une application Web line-of-business.  
  
 Une fois que vous avez configuré la page ASPX, vous la page de démarrage et entrez les paramètres pour un message : l’accueil et les organisations partenaires ; l’ID d’instance ; version et code PIP et la catégorie du message. Vous pouvez ensuite modifier le contenu du service et envoyer le message.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication  
  
## <a name="adding-a-virtual-server-for-lobwebapplication"></a>Ajout d’un serveur virtuel pour LOBWebApplication  
  
#### <a name="to-add-a-virtual-server"></a>Pour ajouter un serveur virtuel  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le Gestionnaire des Services IIS, développez  **\<nom de l’ordinateur\> (ordinateur local)**, développez **Sites Web**, puis cliquez sur **Site Web par défaut**.  
  
3.  Pointez sur **nouveau**, puis cliquez sur **répertoire virtuel**.  
  
4.  Sur le **Assistant de création de répertoire virtuel** , cliquez sur **suivant**, puis tapez un alias pour le site, tel que **LOBWebApplication**.  
  
5.  Sur le **répertoire de contenu du Site Web** , cliquez sur **Parcourir**, atteindre \< *lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication, cliquez sur **OK**, puis cliquez sur **suivant**.  
  
6.  Sur le **autorisations d’accès de répertoire virtuel** page, sélectionnez **en lecture** et **exécuter des scripts**, puis cliquez sur **suivant**. Cliquez sur **Terminer**.  
  
7.  Ajoutez l’utilisateur du compte de service qui a été utilisé pour configurer BTARN, par exemple, hostsvc, à la STS_WPG.  
  
8.  Supprimez tous les fichiers C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files. Vous devrez peut-être exécuter le programme iisreset pour déverrouiller les fichiers avant de les supprimer.  
  
9. Dans le Gestionnaire des services Internet, définissez LOBWebApplication pour s’exécuter sous le BTARNHTTPReceivePool du Pool d’applications.  
  
10. Dans le Gestionnaire des services Internet, dans la section Propriétés de sécurité de répertoire de l’utilitaire LOBWebApplication, désactivez l’option pour le répertoire virtuel exécuter en tant qu’utilisateur anonyme.  
  
## <a name="building-lobwebapplication"></a>Construction LOBWebApplication  
  
#### <a name="to-build-lobwebapplication"></a>Pour générer des LOBWebApplication  
  
1.  Démarrez Visual Studio.  
  
2.  Sur le **fichier**, pointez sur **ouvrir**, puis cliquez sur **ouvrir une Solution**.  
  
3.  Déplacer vers \< *lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication, sélectionnez **LOBWebApplication.sln**, puis cliquez sur  **Ouvrez**.  
  
    > [!NOTE]
    >  Si vous n’avez pas ajouté un serveur virtuel de LOBWebApplication, la solution ne s’ouvre pas correctement dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
4.  Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur **Parcourir**, atteindre \< *lecteur*\>: \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\Bin, sélectionnez les fichiers Microsoft.Solutions.BTARN.ConfigurationManager.dll et Microsoft.Solutions.BTARN.Shared.dll, puis cliquez sur **ouvrir**.  
  
6.  Avec le bouton droit **LOBWebApplication**, puis cliquez sur **Build**.  
  
## <a name="running-lobwebapplication"></a>LOBWebApplication en cours d’exécution  
  
#### <a name="to-run-lobwebapplication-and-submit-a-message"></a>Pour exécuter LOBWebApplication et envoyer un message  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Internet Explorer**.  
  
2.  Dans Internet Explorer, dans le **adresse** zone, tapez http://localhost/LOBWebApplication, puis cliquez sur **accédez**.  
  
3.  Dans le **envoyer un Message** boîte de dialogue, tapez l’organisation d’origine, l’organisation partenaire, le code PIP, la version PIP, l’ID d’Instance PIP et la catégorie du message.  
  
4.  Modifiez le contenu de service en fonction des besoins.  
  
5.  Cliquez sur **Envoyer**.  
  
## <a name="remarks"></a>Notes  
 L’utilitaire LOBWebApplication génère une instance du message à partir du PIP spécifié et insère le contenu du service à partir de l’instance de message généré dans la page ASPX. Pour ce faire, l’utilitaire utilise la même technique qu’il utilise pour générer une instance de message bien formée directement à partir d’une adresse PIP. Pour plus d’informations, consultez [création d’une Instance de Message bien formée à partir d’une adresse PIP](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md). Vous pouvez remplir n’importe quel champ du contenu de service dans la page ASPX avec des données réelles pour générer une instance de message réel.  
  
 Vous utilisez l’utilitaire LOBWebApplication pour simuler une application Web de métier-envoi d’un message. Vous utilisez l’utilitaire LOBApplication pour simuler une application de bureau métier-envoi d’un message.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)