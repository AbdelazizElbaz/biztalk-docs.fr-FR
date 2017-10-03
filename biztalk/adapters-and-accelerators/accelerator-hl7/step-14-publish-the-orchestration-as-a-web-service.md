---
title: "Étape 14 : Publier l’Orchestration en tant que Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- publishing, orchestrations
- Web services, orchestrations
- message enrichment tutorial, orchestrations
- publishing, Web services
- message enrichment tutorial, Web services
ms.assetid: 8f29a7be-a679-4ca6-a648-35338d9e9e98
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd7707ded0951eb1141368a91e7fe8f533e8241a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-14-publish-the-orchestration-as-a-web-service"></a>Étape 14 : Publier l’Orchestration en tant que Service Web
Dans cette étape, vous utilisez l’Assistant de publication des Services Web BizTalk pour publier une orchestration en tant que service Web.  
  
 Avant de publier l’orchestration en tant qu’un service Web, vous devez vous assurer que le compte d’ouverture de session pour BizTalkServerIsolatedHost fait partie du groupe utilisateurs d’hôtes BizTalk isolés, elle a accès aux bases de données BizTalk. Cela est nécessaire car le Gestionnaire de réception pour l’emplacement de réception SOAPReceivePort qui est créé par l’Assistant Publication de services Web pour ce didacticiel est BizTalkServerIsolatedHost, pas BizTalkServerApplication. Le Gestionnaire de réception est BizTalkServerIsolatedHost car l’adaptateur SOAP s’exécute sous le processus IIS, pas le processus BizTalk.  
  
### <a name="to-ensure-access-privileges-for-the-soapreceiveport-receive-location"></a>Pour garantir l’accès des privilèges pour le SOAPReceivePort emplacement de réception  
  
1.  Dans la Console Administration de BizTalk Server, sous **Instances d’hôte** dans les **paramètres de plateforme** nœud, avec le bouton droit **BizTalkServerIsolatedHost**, puis cliquez sur  **Propriétés**. Dans la boîte de dialogue Propriétés, cliquez sur **configurer**. Remarque la **ouverture de session** compte.  
  
2.  Dans la boîte de dialogue Gestion de l’ordinateur sous **groupes** dans les **utilisateurs et groupes locaux** nœud, double-cliquez sur **utilisateurs d’hôtes BizTalk isolés**. Si l’ouverture de session du compte pour **BizTalkServerIsolatedHost** n’est pas un membre de **BizTalkServerIsolatedHost**, ajoutez-le au groupe.  
  
### <a name="to-run-the-biztalk-web-services-publishing-wizard"></a>Pour exécuter l’Assistant de publication des Services Web BizTalk  
  
1.  Dans l’Explorateur de solutions de Visual Studio, cliquez sur **Solution 'BTAHL7V22Common'**. Sur le **outils** menu, cliquez sur **Assistant Publication des Services Web BizTalk**.  
  
2.  Dans le **Assistant Publication des Services Web BizTalk**, dans le **Bienvenue** , cliquez sur **suivant**.  
  
3.  Sur le **créer un Service Web** page, sélectionnez **publier des orchestrations BizTalk en tant que services web**, puis cliquez sur **suivant**.  
  
4.  Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\*.dll)** champ, tapez ou recherchez  **\<* lecteur*> : \Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**, cliquez sur **BTAHL7 Project.dll**, cliquez sur **ouvrir**, puis cliquez sur **suivant**.  
  
5.  Sur le **Orchestrations et Ports** , vérifiez que tous les nœuds sont sélectionnés, puis cliquez sur **suivant**.  
  
6.  Sur le **propriétés du Service Web** page, pour **espace de noms cible du service web**, type **http://localhost**, puis cliquez sur **suivant**.  
  
7.  Sur le **projet de Service Web** page, sélectionnez **autorise l’accès anonyme au service web** et **BizTalk de créer les emplacements de réception dans l’application suivante**. Sélectionnez **BizTalk Application 1** pour l’application. Conserver la valeur par défaut dans le **emplacement** champ. Cliquez sur **suivant** pour accepter l’emplacement par défaut du projet.  
  
8.  Sur le **résumé du projet de Service Web** , cliquez sur **créer** pour générer le projet de Service Web ASP.NET.  
  
9. Cliquez sur **Terminer** pour fermer l'Assistant.  
  
10. Ouvrez la console Administration de BizTalk Server. Dans la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1** .  
  
11. Cliquez sur **emplacements de réception**, avec le bouton droit **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, puis cliquez sur **propriétés**.  
  
12. Dans la boîte de dialogue Propriétés de l’emplacement de réception, cliquez sur **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLReceive** dans la liste déroulante, puis cliquez sur **OK**.  
  
13. Avec le bouton droit **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, puis cliquez sur **activer**.  
  
 Passez à [étape 15 : configurer l’envoi et de Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)