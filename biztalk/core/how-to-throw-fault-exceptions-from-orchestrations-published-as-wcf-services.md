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
# <a name="how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services"></a>Levée d'exceptions d'erreur à partir d'orchestrations publiées en tant que services WCF
Deux types d’erreurs SOAP peuvent être envoyés à partir d’une orchestration : typé et les erreurs SOAP. Erreurs SOAP typées sont celles dans lesquelles une opération comporte un **System.ServiceModel.FaultContractAttribute** qui spécifie un type d’erreur SOAP personnalisé. Les erreurs SOAP non typées sont celles qui ne sont pas spécifiées dans le contrat pour une opération.  
  
 Les adaptateurs WCF ne prennent pas en charge le traitement des exceptions de contrat d'erreurs typées pour les orchestrations publiées en tant que services WCF. Toutefois, les erreurs SOAP non typées peuvent être renvoyées par des orchestrations ou des pipelines. Pour retourner une erreur SOAP non typée, vous devez définir le **System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults** sur l’emplacement de réception, ou dans le fichier de configuration pour autoriser les clients WCF pour obtenir des informations à propos des exceptions d’opération de service interne.  
  
 Le code suivant illustre la définition de la propriété dans un fichier de configuration :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Comment gérer les contrats d’erreurs typées dans les Orchestrations](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)