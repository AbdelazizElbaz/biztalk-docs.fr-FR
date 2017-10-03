---
title: "Dans SAP à l’aide du modèle de Service WCF de réception entrant tRFC appels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving inbound using the WCF service model
- WCF service model, receiving inbound tRFC calls
ms.assetid: 02dc282b-b659-466a-8bd1-f400a05f71ec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fb2091d0701831985a1975aa33bd5ecb667b443
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model"></a>Réception entrant tRFC appelle dans SAP à l’aide du modèle de Service WCF
Vous pouvez utiliser la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] comme serveur RFC (tRFC) transactionnels pour recevoir les appels entrants tRFC à partir de SAP. Pour le trafic entrant tRFCs, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge plusieurs tRFCs dans la même unité logique de SAP de travail (LUW).  
  
 Les sections de cette rubrique fournissent des informations sur l’utilisation de la carte en tant que tRFC serveur dans le modèle de service WCF.  
  
 Vous trouverez plus d’informations sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme serveur tRFC dans les rubriques suivantes :  
  
-   Pour une vue d’ensemble de la prise en charge pour tRFCs sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). Vous devez lire cette rubrique avant de continuer.  
  
-   Pour plus d’informations sur les schémas de message pour les opérations de serveur tRFC, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
## <a name="the-wcf-service-contract-for-a-trfc"></a>Le contrat de Service WCF pour un tRFC  
 Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un contrat de service WCF pour le tRFCs que vous souhaitez recevoir à partir du système SAP. Le contrat généré pour un tRFC entrant est similaire à celui généré par une commande RFC entrante, sauf que :  
  
-   les opérations tRFC sont signalées sous le nœud TRFC.  
  
-   Le contrat de service WCF (interface) généré pour tRFCs entrant est nommé « Trfc ». Vous devez spécifier cette interface lorsque vous ajoutez le point de terminaison de service à l’hôte de service. C’est également l’interface que votre service WCF doit implémenter.  
  
    ```  
    public interface Trfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Trfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD/response")]  
        Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
    }  
    ```  
  
-   Le contrat de message de demande pour les opérations TRFC a un paramètre GUID. Il s’agit de GUID qui mappe vers le TID SAP pour le tRFC. Dans les opérations de serveur tRFC, l’adaptateur gère tous les appels à la validation, la restauration et confirmer le TID par le système SAP, donc il est inutile d’utiliser explicitement de ce GUID. Toutefois, vous pouvez l’utiliser pour récupérer le TID SAP à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en appelant **SapAdapterUtilities.ConvertGuidToTid**. Cela peut être utile pour vous aider à résoudre les problèmes sur le système SAP.  
  
    ```  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Trfc/", IsWrapped=true)]  
    public partial class Z_RFC_MKD_ADDRequest {  
  
        ...  
  
        public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y, System.Guid TransactionalRfcOperationIdentifier) {  
            this.DEST = DEST;  
            this.X = X;  
            this.Y = Y;  
            this.TransactionalRfcOperationIdentifier = TransactionalRfcOperationIdentifier;  
        }  
    }  
  
    ```  
  
## <a name="how-do-i-enable-the-adapter-to-act-as-a-trfc-server"></a>Comment activer l’adaptateur pour agir comme un serveur tRFC ?  
 Pour activer l’adaptateur d’agir en tant que tRFC serveur, vous devez définir le **TidDatabaseConnectionString** liaison de propriété à la chaîne de connexion pour la base de données TID. Vous devez le faire avant d’ouvrir l’hôte de service. Il s’agit de la base de données dans laquelle l’adaptateur stocke la transaction SAP ID (TID) pour chaque tRFC. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## <a name="how-do-i-enlist-in-the-transaction-for-inbound-trfcs"></a>Comment inscrire la transaction de tRFCs entrant ?  
 Une SAP logique unité de travail (LUW) peut contenir plusieurs tRFCs. Sur le système SAP, un LUW est identifié par un ID de Transaction unique (TID). L’adaptateur crée une transaction validable pour chacun du TID par le système SAP lorsqu’il appelle tRFC des appels sur la carte. Lorsque le système SAP appelle un tRFC sur la carte ; l’adaptateur transmet la transaction associée le TID SAP à votre service. Vous pouvez accéder à cette transaction en tant que la transaction ambiante d’à l’intérieur de votre méthode d’opération. En inscrivant dans cette transaction ambiante, les actions effectuées dans l’opération peuvent participer à la LUW SAP.  
  
 Pour inscrire dans la transaction ambiante dans une méthode d’opération, vous devez :  
  
1.  Annoter la méthode d’opération avec le **TransactionScopeRequired** propriété de la **OperationBehavior** attribut. Cela indique à WCF que vous souhaitez accéder à la transaction ambiante d’à l’intérieur de l’opération.  
  
2.  Créer une étendue de transaction soit en annotant la méthode d’opération avec le **TransactionAutoComplete** propriété de la **OperationBehavior** attribut ou en utilisant explicitement un  **TransactionScope** à l’intérieur de la méthode d’opération.  
  
 L’exemple suivant montre un service qui implémente les deux opérations. Les deux méthodes d’opération sont annotés avec les **TransactionScopeRequired** propriété pour accéder à la transaction ambiante.  
  
-   **Z_TRFC_EXAMPLE1** explicitement s’inscrit dans la transaction en utilisant un **TransactionScope** objet.  
  
-   **Z_TRFC_EXAMPLE2** est annoté avec le **TransactionAutoComplete** propriété à inscrire dans la transaction  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, UseSynchronizationContext = false)]  
class Z_Example_ServiceContractClass : Trfc  
{  
  
    // This operation method explicitly creates a TransactionScope to enlist in the ambient transaction  
    // You must explictly call ts.Complete to complete the transaction before you return from the operation  
    // Otherwise the transaction is aborted.  
    // You can throw an exception or return without calling ts.complete to abort the transacation  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public Z_TRFC_EXAMPLE1Response Z_TRFC_EXAMPLE1(Z_TRFC_EXAMPLE1Request request)  
    {  
        using (TransactionScope ts = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Process tRFC  
  
            ...  
  
            Z_TRFC_EXAMPLE1Response response = new Z_TRFC_EXAMPLE1Response();  
            response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
            return response;  
            //since there is no ts.Complete(), this is equivalent to a rollback.  
        }  
    }  
  
    // This operation method sets the TransactionAutoComplete property of the OperationBehavior attribute  
    // to enlist in the transaction. There is no need to explictly create a TransactionScope in the code.  
    // If the method returns with no unhandled exceptions, the transaction completes; otherwise it aborts  
    // You can throw an exception to abort the transaction.  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public Z_TRFC_EXAMPLE2Response Z_TRFC_EXAMPLE2(Z_TRFC_EXAMPLE2Request request)  
    {  
        // Process tRFC  
  
        ...  
  
        Z_TRFC_EXAMPLE2Response response = new Z_TRFC_EXAMPLE2Response();  
        response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
        return response;  
        //if there is no unhandled exception, the transaction completes when the operation returns.  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)