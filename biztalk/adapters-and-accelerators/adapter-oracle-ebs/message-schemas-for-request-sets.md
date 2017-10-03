---
title: "Schémas de message de demande définit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bba9677d-ee94-4da5-8611-b1e47f2f3798
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fd81ee75088b41a182c5a2aa675266420f8f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-request-sets"></a>Schémas de message pour les ensembles de requêtes
Chaque requête définie dans une application Oracle dans Oracle E-Business Suite est présenté comme une opération dans [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## <a name="message-structure-of-request-set-operation"></a>Opération de définition de Structure de message de demande  
 Les opérations exposées en surface pour l’ensemble de la demande suivent un modèle d’échange de message demande-réponse. Le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|[Request_Set_Name] Demande|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name] xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]/">   <SetRelClassOptions>     <Application>[value]</Application>     <ClassName>[value]</ClassName>     <CancelOrHold>[value]</CancelOrHold>     <StaleDate>[value]</StaleDate>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRelClassOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <SetNlsOptions>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetNlsOptions>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_NAME1]>[value]</[CONCURRENT_PROGRAM_NAME1]>   <[CONCURRENT_PROGRAM_NAME2]>[value]</[CONCURRENT_PROGRAM_NAME2]>   … </[Request_Set_Name]>`|-L’opération [Request_Set_Name] prend cinq paramètres standards : `SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions`, `SetNlsOptions`, et `StartTime`.<br /><br /> -La `ContinueOnFail` paramètre indique si l’envoi de la demande set doit continuer ou lever une exception dans le cas le paramètre parent (`SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions` ou `SetNlsOptions`) échoue. Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).<br /><br /> -Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur des ensembles de demande](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).|  
|[Request_Set_Name] Réponse|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name]Response xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]">   <[Request_Set_Name]Result>[value]</[Request_Set_Name]Result> </[Request_Set_Name]Response>`|La réponse à partir d’Oracle E-Business Suite contient un ID de demandes simultanées.|  
  
 Descriptions de l’entité :  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 .  
  
 [CONCURRENT_PROGRAM_NAME] = simultanées du programme inclus dans l’ensemble de la demande.  
  
## <a name="message-actions-for-request-sets"></a>Actions de message pour les ensembles de requêtes  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les actions de message suivantes pour les ensembles de requêtes.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Message|Action|Exemple|  
|-------------|------------|-------------|  
|Demande d’ensemble|RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]|RequestSets/SQLGL/FNDRSSUB965|  
|Demande de réponse|RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]] / réponse|RequestSets/SQLGL/FNDRSSUB965/réponse|  
  
 Descriptions de l’entité :  
  
 [APP_SHORT_NAME] = nom court de l’Application.  
  
 [REQUESTSET_SHORT_NAME] = demande un nom court.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)