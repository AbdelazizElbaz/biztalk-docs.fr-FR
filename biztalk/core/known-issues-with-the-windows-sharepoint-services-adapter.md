---
title: "Problèmes connus avec l’adaptateur Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c20eda7-643d-484c-bf5d-59ff69604cea
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09369108d5e122bb8243ac94d2748db7bc1e06f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="5c5ba-102">Problèmes connus avec l'adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="5c5ba-102">Known Issues with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="5c5ba-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="5c5ba-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="5c5ba-104">Known Issues</span></span>  
  
#### <a name="wss-adapter-fails-to-start-a-workflow-attached-to-a-doc-librarysharepoint-list"></a><span data-ttu-id="5c5ba-105">L'adaptateur WSS ne démarre pas un workflow associé à une bibliothèque de documents/liste SharePoint</span><span class="sxs-lookup"><span data-stu-id="5c5ba-105">WSS Adapter Fails to Start a Workflow attached to a Doc Library/Sharepoint List</span></span>  
 <span data-ttu-id="5c5ba-106">Dans le cadre de l'utilisation de l'adaptateur WSS de BizTalk en vue de soumettre un document ou un élément de liste à une bibliothèque de documents/liste SharePoint, celui-ci ne parvient pas à démarrer le workflow associé à cette liste.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-106">When using the WSS Adapter from BizTalk to submit either a document or list item to a Doc Library/Sharepoint List, it fails to start the workflow attached to that List.</span></span> <span data-ttu-id="5c5ba-107">La solution de contournement consiste à copier le code XML suivant dans le fichier \Program Files\Microsoft BizTalk Server 20xx\Business Activity Services\BTSharePointV3AdapterWS\web.config.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-107">The workaround is to copy the XML code below into the \Program Files\Microsoft BizTalk Server 20xx\Business Activity Services\BTSharePointV3AdapterWS\web.config file.</span></span>  <span data-ttu-id="5c5ba-108">Le ci-dessous XML code doit être inséré à l’intérieur de la \<configuration > élément.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-108">The below XML code must be inserted inside of the \<configuration> element.</span></span>  
  
```  
<configSections>  
    <sectionGroup name="System.Workflow.ComponentModel.WorkflowCompiler" type="System.Workflow.ComponentModel.Compiler.WorkflowCompilerConfigurationSectionGroup, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
      <section name="authorizedTypes" type="System.Workflow.ComponentModel.Compiler.AuthorizedTypesSectionHandler, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </sectionGroup>  
  </configSections>  
  <System.Workflow.ComponentModel.WorkflowCompiler>  
    <authorizedTypes>  
      <authorizedType Assembly="System.Workflow.Activities, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Workflow.Runtime, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Namespace="System.Workflow.*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowActivationProperties" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowTaskProperties" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.Workflow" TypeName="SPWorkflowHistoryEventType" Authorized="True" />  
      <authorizedType Assembly="Microsoft.SharePoint.WorkflowActions, Version=12.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" Namespace="Microsoft.SharePoint.WorkflowActions" TypeName="*" Authorized="True" />  
    </authorizedTypes>  
  </System.Workflow.ComponentModel.WorkflowCompiler>  
  
```