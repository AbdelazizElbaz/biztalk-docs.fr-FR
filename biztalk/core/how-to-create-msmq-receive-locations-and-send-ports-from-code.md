---
title: "Créer MSMQ emplacements de réception et Ports d’envoi à partir de Code | Documents Microsoft"
description: "Créer par programmation MSMQ emplacements de réception et ports d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebb4119-deeb-4287-aa65-7597ff0cc435
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d362ae262c7b054bd86fda72f8aacd3b5ab1455
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-msmq-receive-locations-and-send-ports-programmatically"></a>Créer par programme des Ports d’envoi et emplacements de réception MSMQ
Cette rubrique décrit l'utilisation de WMI afin de créer un port ou un emplacement pour l'adaptateur MSMQ.  
  
 Pour plus d’informations, consultez **création d’un emplacement de réception avec un WMI à l’aide de Configuration de planification Datetime** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="setting-property-values"></a>Configuration des valeurs des propriétés  
 Le processus de création d'un port ou d'un emplacement est toujours le même :  
  
1.  Création d'un objet du type approprié.  
  
2.  Définition des valeurs des propriétés sur l'objet.  
  
3.  Validation des valeurs de l'objet dans la base de données.  
  
 Tous les adaptateurs ont certaines propriétés, telles que **nom d’hôte**, en commun. Vous pouvez les définir en les attribuant directement à l'objet. Le code C# suivant illustre un cas classique :  
  
```  
objReceiveLocation["HostName"] = "BizTalkServerApplication";  
```  
  
 Vous attribuez des valeurs aux propriétés qui ne sont pas communes à tous les adaptateurs. Pour ce faire, vous devez créer un document XML dans une chaîne, puis attribuer celle-ci à la propriété CustomCfg. Le code C# suivant illustre un cas classique pour un adaptateur FILE :  
  
```  
objReceiveLocation["CustomCfg"] =   
        @"<CustomProps>"  
        + @"<BatchSize>20</BatchSize>"  
        + @"<FileMask>*.xml</FileMask>"  
        + @"<FileNetFailRetryCount>5</FileNetFailRetryCount>"  
        + @"<FileNetFailRetryInt>5</FileNetFailRetryInt>"  
        + @"</CustomProps>";  
```  
  
 Les noms des balises présentes dans l'élément CustomProps représentent les noms internes que l'adaptateur utilise pour les propriétés.  
  
 L'adaptateur MSMQ possède une balise unique, AdapterConfig, qui se trouve à l'intérieur de la balise CustomProps. La balise AdapterConfig contient une chaîne de balises XML pour les valeurs des propriétés personnalisées incluses dans une balise Config. Toutefois, les balises sont codées : «&lt;« remplace »\<« et »&gt;» remplace « > ». Par exemple, le XML d'un sous-ensemble de l'adaptateur associé à des propriétés MSMQ peut s'afficher comme suit :  
  
```  
<Config>  
    <batchSize>40</batchSize>  
</Config>  
```  
  
 Notez que la **vt** attribut n’est pas utilisé. La chaîne assignée à la **CustomCfg** propriété s’affiche comme suit après avoir :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config><batchSize>40</batchSize></Config></AdapterConfig></CustomProps>  
```  
  
## <a name="custom-property-names"></a>Noms des propriétés personnalisées  
 Le tableau suivant répertorie les noms internes de l’adaptateur MSMQ **envoyer** propriétés personnalisées.  
  
|**Envoyer le nom de propriété personnalisée**|**Nom complet**|  
|-----------------------------------|----------------------|  
|acknowledgeType|Type d'accusé de réception|  
|administrationQueue|File d'attente d'administration|  
|certificate|Empreinte de certificat|  
|encryptionAlgorithm|Algorithme de chiffrement|  
|maximumMessageSize|Taille maximale message (en Ko)|  
|password|Mot de passe|  
|priority|Priorité du message|  
|queue|File d’attente de destination|  
|recoverable|Récupérable|  
|segmentationSupport|Prise en charge de la segmentation|  
|sendBatchSize|Taille de lot|  
|sendQueueName|File d’attente de destination|  
|timeOut|Délai d'expiration|  
|timeOutUnits|Unité délai d'expiration|  
|transactionnels|Transactionnelle|  
|useAuthentication|Utiliser l'authentification|  
|useDeadLetterQueue|Utiliser file d'attente messages non distribués|  
|useJournalQueue|Utiliser file d'attente journal|  
|userName|Nom d'utilisateur|  
  
 Le tableau suivant répertorie les noms internes de l’adaptateur MSMQ **réception** propriétés personnalisées.  
  
|**Nom de la propriété personnalisée de réception**|**Nom complet**|  
|--------------------------------------|----------------------|  
|batchSize|Taille de lot|  
|Mot de passe|Mot de passe|  
|File d'attente|File d'attente|  
|serialProcessing|Traitement en série|  
|Transactionnelle|Transactionnelle|  
|userName|Nom d'utilisateur|  
  
## <a name="sample-code"></a>Exemple de code  
 Le programme C# suivant permet de créer un emplacement de réception unique pour l'adaptateur MSMQ. Il considère que le port de réception, à savoir ReceivePort1, existe et utilise une fonction d'assistance pour coder et mettre en forme les propriétés personnalisées.  
  
```  
using System;  
using System.Management;  
using System.Text;  
  
namespace CreateReceive  
{  
    ///   
    /// Program to create a receive location.  
    ///   
    class CreateReceive  
    {  
        /// The main entry point for the application.  
  
        [STAThread]  
        static void Main()  
        {  
            // Custom properties & values  
            string cfg =   
                    @"<queue>FORMATNAME:DIRECT=OS:MYMACHINE02\PRIVATE$\QUEUE2</queue>"  
                    + @"<batchSize>40</batchSize>"  
                    + @"<transactional>true</transactional>"  
                    + @"<serialProcessing>false</serialProcessing>";  
  
            CreateReceiveLocation (  
                    "Code Created Location",  
                    "ReceivePort1",  
                    "MSMQ",  
                    "BizTalkServerApplication",  
                    EncodeCustomProps(cfg),  // Encode the custom props  
                    "Microsoft.BizTalk.DefaultPipelines.PassThruReceive,"   
                            + " Microsoft.BizTalk.DefaultPipelines,"   
                            + " Version=3.0.1.0, Culture=neutral,"   
                            + " PublicKeyToken=31bf3856ad364e35",  
                    @"FORMATNAME:DIRECT=OS:MYMACHINE\PRIVATE$\QUEUE2"  
                );  
  
        }  
  
        static string EncodeCustomProps (string cp) {  
  
            // Enclose the properties and values in a Config> tag.  
            StringBuilder tmp = new StringBuilder( @"<Config>" + cp + @"</Config>");  
  
            // Encode the string  
            tmp = tmp.Replace("<","<");  
            tmp = tmp.Replace(">",">");  
  
            return (  
                // Enclose the encoded string with necessary tags  
                "<CustomProps><AdapterConfig vt=\"8\">"  
                + tmp.ToString()   
                + "</AdapterConfig></CustomProps>");  
  
        }  
  
        static void CreateReceiveLocation (  
            string name,            // Location name  
            string port,            // Receive port, already exists  
            string adapterName,     // The transport type  
            string hostName,        // BTS host  
            string customCfg,       // Encoded custom properties  
            string pipeline,        // Full specification of pipeline  
            string inboundTransport)// Inbound transport url  
        {  
            try   
            {  
                // Create options to store options in management object  
                PutOptions options = new PutOptions();  
                options.Type = PutType.CreateOnly;  
  
                // Create a management object  
                // Get the class  
                ManagementClass objReceiveLocationClass =   
                           new ManagementClass(  
                               "root\\MicrosoftBizTalkServer",   
                               "MSBTS_ReceiveLocation",   
                               null);  
                // Create an instance of the member of the class  
                ManagementObject objReceiveLocation =  
                          objReceiveLocationClass.CreateInstance();  
  
                // Fill in the properties  
                objReceiveLocation["Name"] = name;  
                objReceiveLocation["ReceivePortName"] = port;  
                objReceiveLocation["AdapterName"] = adapterName;  
                objReceiveLocation["HostName"] = hostName;  
                objReceiveLocation["PipelineName"] = pipeline;  
                objReceiveLocation["CustomCfg"] = customCfg;  
                objReceiveLocation["IsDisabled"] = true;  
                objReceiveLocation["InBoundTransportURL"] = inboundTransport;  
  
                // Put the options -- creates the receive location  
                objReceiveLocation.Put(options);  
            }  
            catch (Exception excep)  
            {  
                System.Console.WriteLine("Create Receive Location ({0}) failed - {1}",  
                                                name, excep.Message);  
            }  
        }  
    }  
}  
```