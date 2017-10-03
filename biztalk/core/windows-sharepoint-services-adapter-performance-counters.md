---
title: "Compteurs de performances de l’adaptateur de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41583fde-530a-4070-9647-f1ab6273aadf
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80340fd8479b8bf1a0e431e90778f7501763fe4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter-performance-counters"></a>Compteurs de performances de l'adaptateur Windows SharePoint Services
Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur Windows Sharepoint Services** catégorie d’objet de performances :  
  
|**Catégorie**|**Compteur**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:adaptateur Windows SharePoint Services|% d'échecs de réception de messages|Pourcentage des fichiers Windows SharePoint Services non traités par BizTalk Server en raison d'erreurs lors de la réception.|  
||% d'échecs d'envoi de messages|Pourcentage de messages dont l'envoi par BizTalk Server à Windows SharePoint Services a échoué.|  
||% d'échecs d'appel du service Web|Pourcentage des appels du service Web de l'adaptateur Windows SharePoint Services qui ont échoué.|  
||Total d'échecs de validation des réceptions|Nombre total d'erreurs Windows SharePoint Services détectées lors de la mise à jour de l'état des documents SharePoint.|  
||Total d'échecs de réception de messages|Nombre total des fichiers Windows SharePoint Services reçus qui n'ont pas été traités par BizTalk Server en raison d'erreurs.|  
||Total de messages reçus|Nombre total des fichiers Windows SharePoint Services reçus par l'adaptateur Windows SharePoint Services, comprenant les fichiers dont le traitement a échoué.|  
||Total d'échecs d'envoi de messages|Nombre total de messages dont l'envoi par BizTalk Server à Windows SharePoint Services a échoué.|  
||Total de messages envoyés|Nombre total de messages envoyés par BizTalk Server à Windows SharePoint Services, comprenant les fichiers dont le traitement a échoué.|  
||Total d'échecs d'appel du service Web|Nombre total des appels du service Web de l'adaptateur Windows SharePoint Services qui ont échoué.|  
||Appels du service Web par seconde|Nombre total des appels du service Web de l'adaptateur Windows SharePoint Services par seconde.|  
  
## <a name="to-access-performance-counters"></a>Pour accéder aux compteurs de performance  
 Utilisez la procédure suivante pour accéder aux compteurs de performances.  
  
#### <a name="if-you-are-using-windows-2008"></a>Si vous exécutez Windows 2008  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.  
  
2.  Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.  
  
3.  Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **adaptateur Windows Sharepoint Services** objet compteur de performance et sélectionnez les compteurs à surveiller  
  
4.  Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.  Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.  
  
5.  Après avoir ajouté les compteurs, cliquez sur **OK**.  
  
     Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.