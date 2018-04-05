---
title: Référence de message pour le Service orienté solutions | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, message reference
ms.assetid: 47b56d83-799d-444d-b7ef-c2db56a0e470
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2415fd7e48c3936520d7669a80a357094266c56
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-reference-for-the-service-oriented-solution"></a>Référence des messages de la solution orientée services
Cette section répertorie les messages et types de messages utilisés par chaque orchestration dans la solution. Ces éléments sont répertoriés par version d'application.  
  
## <a name="adapter-version"></a>Version d'adaptateur  
 Dans la table, \<SolutionPrefix\> remplace Microsoft.Samples.BizTalk.woodgrovebank pour simplifier la mise en forme de la table sa.  
  
 Les orchestrations, les messages et les types sont les suivants :  
  
|Orchestration|Message|Type de message|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>. Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>. Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>. Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_. GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>. Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_. GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>. Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>. Schemas.PendingTransactionsResponse|  
|CustomerService.odx|StubSAPWebServiceRequest|\<SolutionPrefix\>. Orchestrations.Adapter.StubSAPWS.StubSAPWS_. GetAccountDetails_request|  
|CustomerService.odx|StubSAPWebServiceResponse|\<SolutionPrefix\>. Orchestrations.Adapter.StubSAPWS.StubSAPWS_. GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
  
## <a name="adapter-with-sap-version"></a>Adaptateur avec version SAP  
 Dans la table, \<SolutionPrefix\> remplace Microsoft.Samples.BizTalk.woodgrovebank pour simplifier la mise en forme de la table sa.  
  
 Les orchestrations, les messages et les types sont les suivants :  
  
|Orchestration|Message|Type de message|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>. Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>. Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>. Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_. GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>. Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_. GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>. Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>. Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
  
## <a name="inline-version"></a>Version Inline  
 Dans la table, \<SolutionPrefix\> remplace Microsoft.Samples.BizTalk.WoodgroveBank pour aider à la mise en forme de la table.  
  
 Les orchestrations, les messages et les types sont les suivants :  
  
|Orchestrations|Message|Type de message|  
|--------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>. Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>. Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>. Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>. Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|LastPaymentRequestAfterSendPipeline|System.Xml.XmlDocument|  
|CustomerService.odx|LastPaymentResponseBeforeReceivePipeline|System.Xml.XmlDocument|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
  
## <a name="stub-version"></a>Version stub  
 Dans la table, \<SolutionPrefix\> remplace Microsoft.Samples.BizTalk.WoodgroveBank pour aider à la mise en forme de la table.  
  
 Les orchestrations, les messages et les types sont les suivants :  
  
|Orchestration|Message|Type de message|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>. Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>. Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>. Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_. GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>. Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_. GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>. Schemas.BAPI_BANKACCT_GET_DETAIL. BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>. Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>. Schemas.PendingTransactionsResponse|  
|CustomerService.odx|PaymentTrackerWSRequest|\<SolutionPrefix\>. Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_. GetLastPayments_request|  
|CustomerService.odx|PaymentTrackerWSResponse|\<SolutionPrefix\>. Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_. GetLastPayments_response|  
|CustomerService.odx|StubSAPWSRequest|\<SolutionPrefix\>. Orchestrations.Stubbed.StubSAPWS.StubSAPWS_. GetAccountDetails_request|  
|CustomerService.odx|StubSAPWSResponse|\<SolutionPrefix\>. Orchestrations.Stubbed.StubSAPWS.StubSAPWS_. GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>. Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>. Schemas.CustomerServiceResponse|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la solution orientée services](../core/service-oriented-solution-reference.md)