---
title: "Levée des Exceptions d’erreur à partir d’Orchestrations publiées en tant que Services WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, WCF services
- WCF services, orchestrations
- WCF services, errors
- orchestrations, WCF services
ms.assetid: 89f57841-d40e-4a5a-90a8-5556a2766c03
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bf64501f619e74991fafa59b2ab1c2a3e62cbca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services"></a><span data-ttu-id="68d60-102">Levée d'exceptions d'erreur à partir d'orchestrations publiées en tant que services WCF</span><span class="sxs-lookup"><span data-stu-id="68d60-102">How to Throw Fault Exceptions from Orchestrations Published as WCF Services</span></span>
<span data-ttu-id="68d60-103">Deux types d’erreurs SOAP peuvent être envoyés à partir d’une orchestration : typé et les erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="68d60-103">Two types of SOAP faults can be sent from an orchestration: typed and untyped SOAP faults.</span></span> <span data-ttu-id="68d60-104">Erreurs SOAP typées sont celles dans lesquelles une opération comporte un **System.ServiceModel.FaultContractAttribute** qui spécifie un type d’erreur SOAP personnalisé.</span><span class="sxs-lookup"><span data-stu-id="68d60-104">Typed SOAP faults are those in which an operation has a **System.ServiceModel.FaultContractAttribute** that specifies a custom SOAP fault type.</span></span> <span data-ttu-id="68d60-105">Les erreurs SOAP non typées sont celles qui ne sont pas spécifiées dans le contrat pour une opération.</span><span class="sxs-lookup"><span data-stu-id="68d60-105">Untyped SOAP faults are those that are not specified in the contract for an operation.</span></span>  
  
 <span data-ttu-id="68d60-106">Les adaptateurs WCF ne prennent pas en charge le traitement des exceptions de contrat d'erreurs typées pour les orchestrations publiées en tant que services WCF.</span><span class="sxs-lookup"><span data-stu-id="68d60-106">WCF adapters do not support processing typed fault contract exceptions for orchestrations published as WCF services.</span></span> <span data-ttu-id="68d60-107">Toutefois, les erreurs SOAP non typées peuvent être renvoyées par des orchestrations ou des pipelines.</span><span class="sxs-lookup"><span data-stu-id="68d60-107">However, untyped SOAP faults can always be returned by orchestrations or pipelines.</span></span> <span data-ttu-id="68d60-108">Pour retourner une erreur SOAP non typée, vous devez définir le **System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults** sur l’emplacement de réception, ou dans le fichier de configuration pour autoriser les clients WCF pour obtenir des informations à propos des exceptions d’opération de service interne.</span><span class="sxs-lookup"><span data-stu-id="68d60-108">To return an untyped SOAP fault, you need to set the **System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults** on the receive location, or in the config file, to permit WCF clients to obtain information about internal service operation exceptions.</span></span>  
  
 <span data-ttu-id="68d60-109">Le code suivant illustre la définition de la propriété dans un fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="68d60-109">The following code shows how to set the property in a config file:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="ServiceBehaviorConfiguration">  
                    <serviceDebug includeExceptionDetailInFaults="true" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68d60-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68d60-110">See Also</span></span>  
 [<span data-ttu-id="68d60-111">Comment gérer les contrats d’erreurs typées dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="68d60-111">How to Handle Typed Fault Contracts in Orchestrations</span></span>](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)