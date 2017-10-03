---
title: "Schémas de message pour les programmes simultanés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c5709d5-e2b3-485b-9cdd-004985972ba1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f475fce04e796e633359c846c339f521b6f74a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-concurrent-programs"></a>Schémas de message pour les programmes simultanés
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]met en évidence des programmes simultanés en tant qu’opérations. En même temps que les programmes simultanés exposées en tant qu’opérations, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] met également en évidence les trois opérations standards suivantes : Get_Status, Wait_For_Request et Submit_Request. Pour plus d’informations sur ces opérations liées aux programmes simultanés, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).  
  
## <a name="message-structure-of-concurrent-program-operations"></a>Structure d’opérations simultanées de programme  
 Les opérations exposées en surface pour des programmes simultanés suivent un modèle d’échange de message demande-réponse. Le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|[Concurrent_Program_Name] Demande|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name] xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]/">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <Description>[value]</Description>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_ARGUMENT1]>[value]</[CONCURRENT_PROGRAM_ARGUMENT1]>   <[CONCURRENT_PROGRAM_ARGUMENT2]>[value]</[CONCURRENT_PROGRAM_ARGUMENT2]>   … </[Concurrent_Program_Name]>`|-L’opération [Concurrent_Program_Name] prend cinq paramètres standards : *SetOptions*, *SetPrintOptions*, *SetRepeatOptions*, *Description* , et *StartTime*.<br /><br /> -La *ContinueOnFail* paramètre indique si l’envoi de demandes simultanées doit continuer dans les cas le paramètre parent (*SetOptions*, *SetPrintOptions* ou *SetRepeatOptions*) échoue, ou si elle doit lever une exception. Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).<br /><br /> -Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|[Concurrent_Program_Name] Réponse|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name]Response xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <[Concurrent_Program_Name]Result>[value]</[Concurrent_Program_Name]Result> </[Concurrent_Program_Name]Response>`|La réponse à partir d’Oracle E-Business Suite contient un ID de demandes simultanées.|  
|Get_Status demande|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>  </GetStatusForConcurrentProgram>`|Ce message de demande de Get_Status prend l’ID de demande d’un programme simultané en tant qu’entrée.|  
|Get_Status réponse|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <GetStatusForConcurrentProgramResult>[value]</GetStatusForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>  </GetStatusForConcurrentProgramResponse>`|Ce message de réponse Get_Status retourne la phase/état de la demande et le message d’achèvement d’un programme simultané.<br /><br /> Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Demande de Wait_For_Request|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>   <Interval>[value]</Interval>   <MaxWait>[value]</MaxWait>    </WaitForRequestForConcurrentProgram>`|Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Réponse de Wait_For_Request|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <WaitForRequestForConcurrentProgramResult>[value]</WaitForRequestForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>    </WaitForRequestForConcurrentProgramResponse>`|Ce message de réponse Wait_For_Request retourne la phase/état de la demande et le message d’achèvement d’un programme simultané.<br /><br /> Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Demande de Submit_Request|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>     <Program>[value]</Program>   <Description>[value]</Description>   <StartTime>[value]</StartTime>   <Arguments>[array_of_strings</Arguments>    </SubmitRequestForConcurrentProgram>`|Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Réponse de Submit_Request|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SubmitRequestForConcurrentProgramResult>[value]</SubmitRequestForConcurrentProgramResult>  </SubmitRequestForConcurrentProgramResponse>`|Si la requête d’envoi se termine correctement, le message de réponse renvoie l’ID de demandes simultanées. Sinon, elle retourne « 0 ».|  
  
 Descriptions de l’entité :  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 [APP_SHORT_NAME] = nom court de l’Application  
  
 [CONCURRENT_PROGRAM_ARGUMENT] = Argument attendu par le programme simultané, tel que défini dans Oracle E-Business Suite  
  
## <a name="message-actions-for-concurrent-programs"></a>Actions de message pour les programmes simultanés  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les actions de message suivantes pour les programmes simultanés.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Message|Action|Exemple|  
|-------------|------------|-------------|  
|[Concurrent_Program_Name] Demande|ConcurrentPrograms / [APP_SHORT_NAME] / [CONCURRENT_PROGRAM_SHORT_NAME]|ConcurrentPrograms/SQLGL/ADSFINS|  
|[Concurrent_Program_Name] Réponse|ConcurrentPrograms / [APP_SHORT_NAME] / [CONCURRENT_PROGRAM_SHORT_NAME] / réponse|ConcurrentPrograms/SQLGL/ADSFINS/réponse|  
|Get_Status demande|ConcurrentPrograms / [APP_SHORT_NAME] / GetStatusForConcurrentProgram|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram|  
|Get_Status réponse|ConcurrentPrograms / / GetStatusForConcurrentProgram/réponse de [APP_SHORT_NAME]|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram/réponse|  
|Demande de Wait_For_Request|ConcurrentPrograms / [APP_SHORT_NAME] / WaitForRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram|  
|Réponse de Wait_For_Request|ConcurrentPrograms / / WaitForRequestForConcurrentProgram/réponse de [APP_SHORT_NAME]|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram/réponse|  
|Demande de Submit_Request|ConcurrentPrograms / [APP_SHORT_NAME] / SubmitRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram|  
|Réponse de Submit_Request|ConcurrentPrograms / / SubmitRequestForConcurrentProgram/réponse de [APP_SHORT_NAME]|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram/réponse|  
  
 Descriptions de l’entité :  
  
 [APP_SHORT_NAME] = nom court de l’Application  
  
 [CONCURRENT_PROGRAM_SHORT_NAME] = nom court de simultanées du programme  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)