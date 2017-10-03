---
title: "Instrumentation d’une Solution : utilisation de l’API détaillées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9e027ab-1927-4905-8970-8061ac55d591
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73c59ab28c228c779fd9e6e84d836b87415d6386
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instrumenting-a-solution-step-by-step-api-usage"></a>Instrumentation d’une Solution : utilisation de l’API pas à pas
Cette rubrique décrit la procédure d'instrumentation d'une application à l'aide de la classe clé de l'API BAM. Dans les extraits suivants, nous avons simplifié l'exemple de code, en utilisant des constantes, ainsi que le code minimal nécessaire pour instrumenter une application.  
  
 L'extrait de code suivant montre comment créer un objet [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) , en particulier [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx). Dans cet extrait, le premier paramètre spécifie la chaîne de connexion vers la banque de données de la base de données d'importation principale BAM. Le deuxième paramètre indique la fréquence à laquelle les événements sont inscrits dans la banque de données.  
  
> [!NOTE]
>  BAM prend en charge les connexions vers les banques de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] uniquement. L'exemple de chaîne de connexion représente la chaîne minimale requise pour établir une connexion. Votre configuration nécessitera peut-être la spécification d'autres paramètres dans la chaîne de connexion.  
  
 Une valeur *FlushThreshold* de 0 indique que les événements ne sont pas automatiquement inscrits et que vous devez appeler la méthode Flush pour les inscrire. La valeur un entraîne l'inscription de tous les événements au moment où ils surviennent. Les valeurs supérieures à un indiquent que les événements sont inscrits lorsqu'un lot a atteint le nombre d'événements défini pour ce faire. L'utilisation d'une valeur supérieure à un peut permettre d'améliorer les performances.  
  
```  
// Specify the DES connection string.  
const string connBAMPIT =  
   "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
// Write the activity update data on every call.  
int flushThreshold = 1;  
// Create a DES instance  
EventStream es =   
   new DirectEventStream(connBAMPIT, flushThreshold);  
```  
  
 Une fois l'objet [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) créé, vous pouvez commencer l'activité et mettre à jour la table d'activité avec les données et étapes majeures collectées. Lorsque l'activité BAM a été déployée, cinq tables ont été créées dans la base de données d'importation principale BAM. Pour plus d’informations sur le processus de développement, consultez [vue d’ensemble du processus de développement BAM](../core/overview-of-the-bam-development-process.md).  
  
 L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) permet d'ajouter un enregistrement à la table bam_ PurchaseOrder_Activity. Le premier paramètre contient le nom de l'activité mise à jour, tandis que le deuxième contient un identificateur pour cette instance de l'activité. L'identificateur peut être une chaîne, mais il doit être unique dans le jeu d'enregistrements de l'activité.  
  
 À ce stade, l'enregistrement ne contient pas de données. La méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) met à jour l'enregistrement à l'aide des données d'événement capturées. À nouveau, vous spécifiez une activité et l'identificateur d'instance de cette activité. Vous transmettez les paires nom-valeur de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) des éléments de données et étapes majeures que vous avez définis dans l'activité. Par exemple, notre activité a défini une étape majeure MS_Received. Lorsque l'activité a été déployée, une colonne de la table bam_ PurchaseOrder_Activity a été créée pour l'étape majeure. L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) spécifie la paire nom-valeur de MS_Received et DateTime.UtcNow pour la mise à jour de l'activité avec la date de réception du bon de commande.  
  
```  
// When a purchase order is received, you call the  
// BeginActivity method in the receive application.  
// You can then capture the event data by calling   
// the UpdateActivity method.  
es.BeginActivity ("PurchaseOrder", "PO123");  
es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
```  
  
 Dans cet exemple, nous continuons vers une deuxième activité. Pour plus d’informations sur les continuations, consultez [Continuation d’activités](../core/activity-continuation.md).  
  
 Pour permettre à d'autres applications instrumentées de mettre à jour l'activité PurchaseOrder, vous incluez un appel à la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) . L'appel spécifie l'activité à laquelle les autres applications peuvent contribuer, l'identificateur de l'instance de l'activité faisant l'objet du suivi, ainsi que le jeton de continuation que les autres applications utilisent pour mettre l'activité à jour. Un enregistrement est inscrit dans la table bam_ PurchaseOrder_continuations pour effectuer le suivi de l'état de la continuation. Si l'activité continue sur d'autres processus, un enregistrement est inscrit pour chaque appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) avec un jeton de continuation.  
  
> [!IMPORTANT]
>  Tous les segments de code d'un scénario de continuation doivent avoir leur propre appel de méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) . Autrement, l'enregistrement de l'activité sera en suspens/orphelin.  
>   
>  Cependant, seul le premier segment (qui utilise l'ID d'activité réel) possède la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) . Les autres segments (qui utilisent leur propre ID de jeton unique) ne doivent pas appeler la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) .  
  
 Après l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) , les autres composants peuvent mettre à jour l'activité de bon de commande à l'aide de [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) en spécifiant le jeton de continuation au lieu de l'ID d'activité. Une fois leurs tâches achevées, les autres composants doivent appeler [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) avec le jeton de continuation pour informer l'infrastructure BAM qu'aucun autre événement n'est prévu.  
  
> [!IMPORTANT]
>  Une fois la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) appelée, une activité peut devenir orpheline si le processus dans lequel cette activité est continuée n'appelle jamais la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) avec le jeton de continuation.  
  
```  
// Continue the activity to the next process that has been  
// instrumented to handle the continuation.  
es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
```  
  
 Pour finir, l'activité est finalisée par l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) spécifiant le nom et l'identificateur de l'activité. Si toutes les continuations sont terminées, l'activité est déplacée dans la table bam_ PurchaseOrder _completed. Les activités peuvent devenir orphelines si les activités de continuation ne se terminent pas.  
  
```  
// Activity from this segment (PO submission) is completed  
es.EndActivity("PurchaseOrder", “PO123”);  
```  
  
 Quand l'activité continue dans un processus distinct, l'application est instrumentée pour mettre à jour la table d'activité avec l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) , en spécifiant le nom de l'activité et le jeton de continuation déclarés dans l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) .  
  
> [!NOTE]
>  Le processus gérant l'activité continuée n'appelle pas la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) . La méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) crée une instance de l'activité en créant les tables de la base de données d'importation principale BAM. Le processus dans lequel l'activité est continuée met à jour l'instance de l'activité déjà existante.  
  
```  
// update when the order is approved  
es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                    DateTime.UtcNow, "T_Product", "Widget");  
  
// update when the product is ready for shipment  
es.UpdateActivity ("PurchaseOrder", “AP123”,  
                   "MS_Ready", DateTime.UtcNow);  
```  
  
 Dans le cadre du workflow de cet exemple, le code indique une référence, dans ce cas, un type précis de référence, à savoir une activité associée. En spécifiant une activité associée, vous créez un lien entre l'activité principale et les autres activités susceptibles d'intéresser l'utilisateur visualisant l'activité dans le portail BAM.  
  
 L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) entraîne l'écriture d'un enregistrement dans la table bam_ PurchaseOrder_ActiveRelationships liant les activités.  
  
```  
// These are shipped in two shipments.  
// Relates the current purchase order   
// instance to two shippings.  
// Note: only one direction  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS101”);  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS102”);  
```  
  
 Pour mettre fin à l'activité continuée, vous appelez la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) en spécifiant le jeton de la continuation qui s'achève. Si toutes les continuations sont terminées, l'activité du bon de commande est déplacée dans la table terminée.  
  
```  
// Activity from this segment (ApprovalProcess) is completed  
es.EndActivity("PurchaseOrder", “AP123”);  
```  
  
## <a name="complete-code-sample"></a>Exemple de code complet  
  
```  
//---------------------------------------------------------------------  
// File:BAMMinimalSample.cs  
//   
// Summary: Demonstrates how to instrument an application   
//using BAM APIs to track useful information.  
//  
// Sample: BAM Api Sample  
//  
//---------------------------------------------------------------------  
// This file is part of the Microsoft BizTalk Server SDK  
//  
// Copyright (c) Microsoft Corporation. All rights reserved.  
//  
// This source code is intended only as a supplement to Microsoft   
// BizTalk Server release and/or on-line documentation. See   
// these other materials for detailed information regarding Microsoft // code samples.  
//  
// THIS CODE AND INFORMATION ARE PROVIDED "AS IS" WITHOUT WARRANTY OF  
// ANY KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO // THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A   
// PARTICULAR PURPOSE.  
//---------------------------------------------------------------------  
// This sample requires that you add the     
// Microsoft.BizTalk.Bam.EventObservation.dll to the   
// references in the Visual Studio Solution.  
  
using System;  
using System.Text;  
using Microsoft.BizTalk.Bam.EventObservation;  
  
namespace EventStreamSample  
{  
  
    static void Main(string[] args)  
    {  
        //   
  // The following code would appear in a purchase order  
   // receipt application.  
        //  
  
        // Specify the DES connection string.  
        const string connBAMPIT =  
            "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
  
        // Write the activity update data on every call.  
        int flushThreshold = 1;  
  
        // Create an instance of the DirectEventStream.  
        EventStream es =   
               new DirectEventStream(connBAMPIT, flushThreshold);  
  
        // When a purchase order is received, you call the  
       // BeginActivity method in the receive application.  
  // You can then capture the event data by calling   
        // the UpdateActivity method.  
        es.BeginActivity ("PurchaseOrder", "PO123");  
        es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
  
   // Continue the activity to the next process that has been  
   // instrumented to handle the continuation.  
        es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
  
        // Activity from this segment (PO submission) is completed  
        // end activity is synonymous to IsCompleted = 1  
        es.EndActivity("PurchaseOrder", “PO123”);  
  
        //  
        // The following code would typically appear in a separate   
        // application that monitors the approval process  
        // (ApprovalProcess.exe)  
        //  
  
        // update when the order is approved  
        es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                            DateTime.UtcNow, "T_Product", "Widget");  
  
        // update when the product is ready for shipment  
        es.UpdateActivity ("PurchaseOrder", “AP123”,  
                            "MS_Ready", DateTime.UtcNow);  
  
        // These are shipped in two shipments.  
        // Relates the current purchase order  
        // instance to two shippings.  
        // Note: only one direction  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS101”);  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS102”);  
  
        // Activity from this segment (ApprovalProcess) is completed  
        es.EndActivity("PurchaseOrder", “AP123”);  
  
        // In another Shipping application, two shipments with  
            ID’s UPS101 and UPS102 will be created.  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md)