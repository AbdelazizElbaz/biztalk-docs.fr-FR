---
title: "Optimisation des performances de l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 437c7325-f037-451a-8dbd-f8d8c8889e20
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbd45901afb229cf884390c2a5120deac0daa90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-orchestration-performance"></a>Optimisation des performances de l’Orchestration
Cette rubrique décrit les meilleures pratiques pour l’utilisation d’orchestrations dans les solutions BizTalk Server. Cela inclut des recommandations pour :  
  
-   Ce qui réduit la latence des solutions BizTalk Server qui utilisent des orchestrations  
  
    -   Élimination des orchestrations pour seulement les modèles de messagerie  
  
    -   Utilisant inline envoie des orchestrations  
  
    -   Réduction des points de persistance d’orchestration  
  
-   Imbrication des orchestrations  
  
-   Modèles de conception d’orchestration  
  
-   Blocs de gestion des exceptions d’orchestration  
  
## <a name="recommendations-for-optimizing-orchestrations-for-low-latency-scenarios"></a>Recommandations pour l’optimisation des orchestrations pour des scénarios à faible latence  
 Les techniques suivantes peuvent être utilisées pour réduire la latence des solutions BizTalk Server qui utilisent des orchestrations.  
  
### <a name="eliminate-orchestrations-for-messaging-only-patterns"></a>Éliminer les orchestrations pour seulement les modèles de messagerie  
 Lorsqu’il est possible de réduire l’utilisation des orchestrations pour augmenter le débit global et de réduire la latence des processus d’entreprise. S’il est inutile d’exécuter longue en cours d’exécution des transactions et il n’est pas nécessaire pour appeler plusieurs systèmes pour chaque demande, puis prendre en compte en éliminant les orchestrations et le déplacement de logique métier pour les Ports d’envoi et réception afin de réduire la quantité totale d’allers-retours vers la BizTalkMsgBoxDb et diminuer la latence en raison de l’accès de la base de données. Dans ce cas, implémentez les pipelines personnalisés et réutiliser les classes d’assistance qui ont été précédemment appelés à partir d’orchestrations. Utilisation des orchestrations uniquement lorsque strictement nécessaire pour implémenter des modèles de conception, à nuages de points et de collecter ou de convois. Pour plus d’informations sur les modèles de conception d’Orchestration, consultez la rubrique [implémentation des modèles de conception dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) dans la documentation de BizTalk Server.  
  
### <a name="use-inline-sends-from-orchestrations-to-accommodate-low-latency-scenarios"></a>Utilisez inline envoie à partir d’orchestrations pour prendre en charge les scénarios de faible latence  
 Chaque fois que possible, réduisez l’utilisation des orchestrations et favoriser des modèles de messagerie seule pour augmenter le débit global et de réduire la latence des processus d’entreprise. Si n’est pas nécessaire pour les transactions à long terme, et il est inutile de logique métier appeler plusieurs systèmes, envisagez de déplacer la logique métier pour les Ports d’envoi et de réception et en supprimant l’utilisation des orchestrations. Cette approche peut être implémentée avec les pipelines personnalisés et qui réutiliser les classes d’assistance qui ont été précédemment appelés à partir d’orchestrations. Afin d’obtenir de meilleures performances dans les scénarios de faible latence, adoptez une des approches suivantes :  
  
-   Éliminer les orchestrations inutiles et adoptent les modèles de messagerie seule afin de réduire la quantité totale d’allers-retours à la base de données MessageBox de BizTalk. Cette approche permet à faible latence, car inline envoie contourner l’associé et moteur de messagerie BizTalk surcharge. Fonctionnalité d’envoi orchestration inline est fournie avec BizTalk Server 2006 et versions ultérieures.  
  
-   Les orchestrations à l’intérieur, éliminer les ports logiques aux ports physiques et l’utilisation en ligne envoie à leur place. Par exemple, un envoi inline utilisable pour créer une instance d’une classe de proxy WCF pour appeler un service Web en aval ou un composant d’ADO.NET pour accéder à une base de données SQL Server. Dans le diagramme suivant, un envoi inline est effectué lorsque l’orchestration instancie un composant métier, qui utilise en interne d’un service WCF objet proxy pour appeler directement un service Web en aval :  
  
     ![Description de l’envoi Inline de l’Orchestration BizTalk](../technical-guides/media/inlinesend.gif "InlineSend")  
  
> [!NOTE]  
>  Bien qu’à l’aide d’envoie inline à partir d’orchestrations réduit considérablement le temps de latence, il existe des limitations de cette approche. Étant donné qu’inline envoie contourner le moteur de messagerie BizTalk, les fonctionnalités suivantes fournies avec le moteur de messagerie ne sont pas disponible :  
>   
>  -   Pipelines transactionnels  
> -   Pipelines récupérables  
> -   Pipelines qui appellent l’API de l’intercepteur BAM  
> -   Prise en charge de l’adaptateur de BizTalk Server  
> -   Traitement par lot  
> -   Tentatives  
> -   L’initialisation du jeu de corrélations  
> -   Configuration déclarative  
> -   Transports secondaires  
> -   Suivi  
> -   Utilisation déclarative de l’analyse BAM  
  
 Pour plus d’informations sur les types de pipelines qui ne peut pas être exécutées à partir d’une orchestration, consultez la section « Limitations » de la rubrique [comment utiliser des Expressions pour exécuter des Pipelines](http://go.microsoft.com/fwlink/?LinkId=158008) (http://go.Microsoft.com/fwlink/?) LinkId = 158008) dans la documentation de BizTalk Server 2010.  
  
### <a name="optimize-orchestration-latency-by-reducing-the-number-of-persistence-points-if-possible"></a>Optimiser la latence de l’orchestration en réduisant le nombre de points de persistance, si possible  
 Une étendue de l’orchestration doit uniquement être marqué comme « transactionnel longue » si vous souhaitez utiliser des délais d’attente de compensation ou de la portée. Une étendue transactionnelle longue provoque un point de persistance supplémentaire à la fin de l’étendue, afin qu’ils doivent être évités lorsque vous n’avez pas besoin d’utiliser la compensation ou les délais d’attente de l’étendue. Une étendue atomique provoque un point de persistance à la fin de l’étendue, mais également garantit qu’aucun point de persistance ne se produira à l’intérieur de l’étendue atomique. Cet effet d’aucune persistance à l’intérieur de l’étendue peut parfois servir à votre avantage pour les points de persistance de lot (lorsque effectuant plusieurs envoie, par exemple). En général, toutefois, nous recommandons d’éviter les étendues atomiques si possible. Le moteur d’orchestration enregistre dans le stockage persistant l’état global d’une instance d’orchestration en cours d’exécution à différents stades, afin que l’instance ultérieurement peut être restauré dans la mémoire et effectuée jusqu'à la fin.   
**Le nombre de points de persistance dans une orchestration est un des principaux facteurs qui influencent la latence des messages transitant via des orchestrations**. Chaque fois que le moteur atteint un point de persistance, l’état interne d’une orchestration en cours d’exécution est sérialisé et enregistré dans la MessageBox et cette opération implique un coût de latence. La sérialisation de l’état interne inclut tous les messages et les variables instancié et pas encore publié dans l’orchestration. Les messages sont volumineux et les variables et les plus le nombre de ces, il sera plus longue pour rendre persistant l’état interne d’une orchestration. Un nombre excessif de points de persistance peut conduire à une dégradation significative des performances. Pour cette raison, nous vous recommandons d’élimination des points de persistance inutiles à partir d’orchestrations en réduisant le nombre d’étendues transactionnelles et formes envoi. Cette approche permet de réduire la contention sur la MessageBox en raison de la mise en attente de l’orchestration et la réactivation, augmenter l’évolutivité globale et de réduire la latence de l’orchestration.   
Un autre recommandation est de toujours conserver l’état interne d’une orchestration aussi petite que possible. Cette technique peut réduire considérablement le temps passé par le moteur XLANG sérialisation, la persistance et la restauration de l’état interne d’une orchestration en cas de point de persistance. Une façon d’effectuer cette opération consiste à créer des variables et les messages plus tard que possible et de libérer les dès que possible ; par exemple, introduisent des étendues non transactionnels à l’intérieur de vos orchestrations et déclarer des variables et des messages au sein de ces étendues internes au lieu de déclarer les au niveau supérieur. Pour plus d’informations sur la limitation des points de persistance d’orchestration, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :  
  
-   [Persistance et le moteur d’Orchestration](http://go.microsoft.com/fwlink/?LinkID=155292) (http://go.microsoft.com/fwlink/?LinkID=155292).  
  
-   [Mise en attente de l’orchestration et la réactivation](http://go.microsoft.com/fwlink/?LinkID=155284) (http://go.microsoft.com/fwlink/?LinkID=155292).  
  
## <a name="guidelines-for-using-promoted-properties-to-access-message-tags-or-attributes-from-an-orchestration"></a>Instructions d’utilisation promues propriétés attributs ou de balises de message d’accès à partir d’une orchestration  
 Si vous n’avez pas besoin de promouvoir des propriétés, promouvoir uniquement les propriétés qui sont utilisées pour le routage des messages, de filtres et de corrélation du message. La promotion de chaque propriété requiert le composant désassembleur (personnalisé de deux dimensions, XML,) pour reconnaître le type de document et récupérer des données à partir du message à l’aide de l’expression XPath de l’annotation relative contenue dans le schéma XSD qui définit le type de document. En outre, chaque promotion de propriété provoque un appel distinct de la procédure stockée de bts_InsertProperty lorsque l’Agent des messages publie le message dans la base de données MessageBox. Si une orchestration doit accéder à un élément ou attribut spécifique contenu dans un document XML, utilisez une des techniques suivantes :  
  
-   Réduisez le nombre de propriétés écrites et promues et supprimer ceux qui ne sont pas strictement nécessaire.  
  
-   Éliminer les champs distinctifs inutiles. Les champs distinctifs sont écrits les propriétés de contexte et peuvent facilement occuper significatifs que leur nom est égal à l’expression XPath qui est utilisée pour récupérer des données. La propriété unique est définie sous forme d’annotations dans le schéma XSD qui définit le type de document. Le composant désassembleur utilise la même approche adoptée pour les propriétés promues et l’expression XPath qui définit un champ unique pour le rechercher dans le document entrant. Ensuite, le composant désassembleur écrit une propriété dans le contexte où :  
  
    -   **Nom**: Expression XPath est définie dans l’annotation.  
  
    -   **Valeur**: valeur de l’élément identifié par l’expression XPath dans un document entrant.  
  
     Les Expressions XPath peuvent être très longues, en particulier lorsque l’élément en question est très profonde du schéma de document. Par conséquent, plus distinguent les champs, plus la taille du contexte. Cela à son tour affecte les performances globales.  
  
-   Utilisez la fonction intégrée XPath fournie par le runtime de l’orchestration.  
  
-   Si les messages sont assez petits (quelques kilo-octets) au format XML, vous pouvez désérialiser le message dans une instance de la classe .NET et travailler avec des champs et propriétés publics. Si le message doit être une élaboration complexe (code personnalisé, les stratégies de moteur de règles métier, etc.) l’accès aux données en utilisant les propriétés exposées par une instance d’une classe .NET est beaucoup plus rapide à l’aide d’expressions XPath. Lorsque la logique métier appelée par l’orchestration est terminée, l’objet d’entité peut être sérialisé dans un message BizTalk. Vous pouvez créer des classes .NET à partir d’un schéma XML à l’aide d’un des outils suivants : l’outil XSD (.NET Framework 2.0) ou SVCUTIL (.NET Framework 3.0).  
  
-   Activer un composant d’assistance à partir d’une orchestration. Cette technique a un avantage par rapport à l’aide des champs distinctifs. En fait, une orchestration peut lire le XPath expression à partir d’une configuration stocker (fichier de configuration, magasin de configuration SSO, base de données personnalisée et ainsi de suite), par conséquent, lorsque vous devez modifier l’expression XPath, vous n’avez pas à modifier et redéployer un schéma, en tant que vous devez effectuer pour les propriétés promues et d champs d’istinguished. L’exemple de code suivant fournit un exemple d’un composant d’assistance. Le composant utilise la classe XPathReader fournie par le moteur d’exécution BizTalk. Ainsi, le code lire le flux de document jusqu'à ce que l’expression XPath est trouvée.  
  
```  
#region Copyright  
//===  
//Microsoft Windows Server AppFabric Customer Advisory Team (CAT)   
//  
// This sample is supplemental to the technical guidance published on the community  
// blog.  
//   
// Author: Paolo Salvatori.  
//===  
// Copyright © 2010 Microsoft Corporation. All rights reserved.  
//   
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER   
// EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF   
// MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. YOU BEAR THE RISK OF USING IT.  
//===  
#endregion  
#region Using Directives  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Xml;  
using System.Linq;  
using System.Text;  
using System.Globalization;  
using Microsoft.XLANGs.BaseTypes;   
using Microsoft.BizTalk.Streaming;  
using Microsoft.BizTalk.XPath;  
#endregion  
namespace Microsoft.AppFabric.CAT.Samples.DuplexMEP.Helpers  
{  
public class XPathHelper  
{  
#region Private Constants   
private const string MessageCannotBeNull = "[XPathReader] The message cannot be null.";  
#endregion  
#region Public Static Methods  
public static string GetValue(XLANGMessage message, int partIndex, string xpath)  
{  
try  
{  
if (message == null)  
{  
throw new ApplicationException(MessageCannotBeNull);  
}  
using (Stream stream = message[partIndex].RetrieveAs(typeof(Stream)) as Stream)  
{  
XmlTextReader xmlTextReader = new XmlTextReader(stream);  
XPathCollection xPathCollection = new XPathCollection();  
XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
xPathCollection.Add(xpath);  
while (xPathReader.Read())  
{  
if (xPathReader.HasAttributes)  
{  
for (int i = 0; i < xPathReader.AttributeCount; i++)  
{  
xPathReader.MoveToAttribute(i);  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.GetAttribute(i);  
}  
}  
}  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.ReadString();  
}  
}  
}  
}  
finally  
{  
message.Dispose();  
}  
return string.Empty;  
}  
#endregion  
}  
}  
```  
  
## <a name="minimize-orchestration-complexity-to-improve-performance"></a>Réduire la complexité d’orchestration pour améliorer les performances  
 La complexité des orchestrations a un impact significatif sur les performances. Avec l’accroissement de complexité de l’orchestration, les performances globales diminuent. Orchestrations peuvent être utilisées dans une diversité presque infinie de scénarios, et chaque scénario peut impliquer des orchestrations de complexité variable. Évitez d’orchestrations complexes lorsque cela est possible en faveur d’une approche modulaire. En d’autres termes, fractionnez votre logique métier en plusieurs orchestrations réutilisables.  
  
 Si vous n’avez pas besoin d’implémenter une orchestration complexe, définissez des messages et des variables dans des étendues internes chaque fois que possible, plutôt qu’au niveau racine. Cette technique conserve un plus faible encombrement en mémoire pour chaque orchestration, car les variables et les messages sont supprimés lorsque le flux quitte l’étendue où les variables et les messages ont été définies. Cette approche est particulièrement utile lorsque les orchestrations sont enregistrées dans la MessageBox à des points de persistance.  
  
## <a name="use-the-call-orchestration-shape-versus-the-start-orchestration-shape-to-improve-performance"></a>La forme appeler Orchestration par rapport à la forme Démarrer Orchestration permet d’améliorer les performances  
 Éviter le **démarrer Orchestration** mettre en forme et utiliser le **appeler Orchestration** forme pour exécuter une orchestration imbriquée. En fait, le **appeler Orchestration** forme peut être utilisée pour appeler de façon synchrone une orchestration qui est référencée dans un autre projet. Cette approche permet la réutilisation des modèles de flux de travail courants d’orchestration pour les projets BizTalk. Quand vous appelez une autre orchestration synchrone avec la **appeler Orchestration** forme, l’orchestration associée attend que l’orchestration imbriquée soit terminée avant de continuer. L’orchestration imbriquée est exécutée sur le même thread que celui qui exécute l’orchestration d’appel.  
  
 Le **démarrer Orchestration** forme est similaire à la **appeler Orchestration** forme, mais dans ce cas, l’orchestration imbriquée est appelée de manière asynchrone : le flux de contrôle dans l’appel orchestration se poursuit au-delà de l’appel, sans attendre que l’orchestration appelée terminer son travail. Pour implémenter ce découplage entre l’appelant et les orchestrations appelées, le **démarrer Orchestration** est implémentée via la publication d’un message dans la BizTalk Messagebox. Ce message est ensuite utilisé par une instance d’hôte BizTalk in-process qui exécute l’orchestration imbriquée. Si possible, utilisez **appeler Orchestration**, surtout si l’orchestration d’appel doit attendre le résultat à partir de l’orchestration imbriquée afin de poursuivre le traitement.  Pour plus d’informations sur l’utilisation de la forme appeler Orchestration, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :  
  
-   [Utilisation de Ports à liaison directe dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139902) (http://go.microsoft.com/fwlink/?LinkId=139902).  
  
-   [Imbrication des Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139903) (http://go.microsoft.com/fwlink/?LinkId=139903).  
  
## <a name="use-xmlreader-with-xlangmessage-versus-using-xmlreader-with-xmldocument-to-improve-orchestration-performance"></a>Utiliser XmlReader avec XLANGMessage et à l’aide de XmlReader avec un XmlDocument pour améliorer les performances de l’orchestration  
 Pour améliorer les performances d’orchestration pour les méthodes .NET appelé à partir d’une orchestration, utilisez XmlReader avec XLANGMessage, pas un XmlDocument. L’exemple de code suivant illustre cette fonctionnalité.  
  
```csharp  
// As a general rule, use XmlReader with XLANGMessage, not XmlDocument.   
// This is illustrated in the parameter passed into the following code.   
// The XLANG/s compiler doesn't allow a return value of XmlReader   
// so documents must be initially constructed as XmlDocument()  
public static XmlDocument FromMsg(XLANGMessage old)  
{  
    //get at the data  
    XmlDocument ret = new XmlDocument();  
  
    try{  
        XmlReader reader = (XmlReader)old[0].RetrieveAs(typeof(XmlReader));  
        //construct new message from old  
        //read property  
        object msgid = old.GetPropertyValue(typeof(BTS.MessageID));  
    }  
    finally {  
        // Call Dispose on the XLANGMessage object   
        // because the message doesn't belong to the   
        // .NET runtime - it belongs to the Messagebox database   
        old.Dispose();  
    }  
    return ret;  
}  
```  
  
 Est une autre méthode pour créer une classe .NET basée sur le schéma. Cette opération prend moins de mémoire que le chargement du document dans un **XmlDocument** objet, ainsi que de fournir un accès facile aux éléments du schéma pour les développeurs .NET. Pour générer une classe basée sur un schéma BizTalk, vous pouvez utiliser l’outil xsd.exe fourni avec Visual Studio. Par exemple, en cours d’exécution **xsd.exe \<schema.xsd >/classes** par rapport à un schéma simple contenant des champs nommés ItemA, ItemB, ItemC, génère la classe suivante.  
  
```csharp  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1433  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
using System.Xml.Serialization;  
  
//   
// This source code was auto-generated by xsd, Version=2.0.50727.42.  
//  
  
/// <remarks/>  
[System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "2.0.50727.42")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://Schemas.MySchema")]  
[System.Xml.Serialization.XmlRootAttribute(Namespace="http://Schemas.MySchema", IsNullable=false)]  
public partial class MySchemaRoot {  
  
    private string itemAField;  
  
    private string itemBField;  
  
    private string itemCField;  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemA {  
        get {  
            return this.itemAField;  
        }  
        set {  
            this.itemAField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemB {  
        get {  
            return this.itemBField;  
        }  
        set {  
            this.itemBField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemC {  
        get {  
            return this.itemCField;  
        }  
        set {  
            this.itemCField = value;  
        }  
    }  
}  
```  
  
 Cette classe peut ensuite être référencée dans votre assembly .NET afin d’accéder aux éléments de message et l’objet retourné peut être directement attribué à un message. Voici un exemple d’utilisation de la classe générée ci-dessus.  
  
```csharp  
public static Root SetValues(Microsoft.XLANGs.BaseTypes.XLANGMessage msg)  
{  
   try  
   {  
   MySchemaRoot rootObj=(MySchemaRoot)msg[0].RetrieveAs(typeof(MySchemaRoot);  
   rootObj.ItemA="value a";  
   rootObj.ItemB="value b";  
   rootObj.ItemC="value c";  
   }  
    finally {  
        msg.Dispose();  
            }  
  
   return rootObj;  
}  
```  
  
 Cette technique vous permet d’utiliser une approche orientée objet lors du traitement des messages. Cette technique doit être utilisée principalement avec relativement petits messages. Effet, même si cette technique utilise beaucoup moins de mémoire que lorsque le chargement du message dans une **XmlDocument** de l’objet, le message entier est toujours chargé en mémoire. Lors du traitement des messages plus volumineux, utilisez le **XmlReader** classe pour lire les messages et les **XmlWriter** classe pour écrire des messages. Lorsque vous utilisez **XmlReader** et **XmlWriter**, le message est contenu dans un **VirtualStream** objet. Si la taille du message dépasse la valeur spécifiée pour **seuil de messages volumineux (en octets)** qui est exposé dans la page de configuration des propriétés du groupe BizTalk, le message est écrit dans le système de fichiers. Cela diminue les performances globales, mais évite les exceptions de mémoire insuffisante.  
  
## <a name="improve-performance-by-minimizing-the-use-of-logical-ports-bound-to-physical-ports"></a>Améliorer les performances en réduisant l’utilisation des ports logiques aux ports physiques  
 Vous pouvez augmenter les performances en réduisant l’utilisation des ports logiques aux ports physiques qui utilisent les adaptateurs suivants :  
  
-   SQL Server, Oracle  
  
-   WSE, HTTP, WCF  
  
-   MSMQ, MQSeries  
  
 Dans BizTalk Server 2010, envoyer et recevoir des pipelines peuvent être appelées directement à partir d’une orchestration à l’aide de la classe XLANGPipelineManager contenue dans le Microsoft.XLANGs.Pipeline.dll. Par conséquent, le traitement des pipelines peut être déplacé à partir des ports à des orchestrations ; les ports logiques dans une orchestration peuvent être remplacés par une forme Expression, ce qui permet d’appeler une instance d’une classe .NET donnée (par exemple, un composant d’accès aux données à l’aide d’ADO.NET). Avant d’adopter cette technique, sachez que si vous n’utilisez pas de cartes et les ports physiques, vous perdez la possibilité de tirer parti de leurs fonctions, telles que le traitement par lot, nouvelles tentatives, une configuration déclarative et transports secondaires.  
  
## <a name="orchestration-design-patterns"></a>Modèles de conception d’orchestration  
 Le Concepteur d’Orchestration permet aux développeurs d’implémenter une large gamme de modèles d’intégration d’entreprise. Certains modèles courants incluent Aggregator, la gestion des exceptions et Compensation, service Broker de Message, à nuages de points et collecte et séquentiel et de convoi parallèle. Ces modèles peuvent être utilisées pour développer des solutions d’intégration d’Application d’entreprise (IAE), Architecture orientée services (SOA) et gestion de processus d’entreprise (BPM) complexes avec BizTalk Server. Pour plus d’informations sur les modèles de conception d’Orchestration, consultez la rubrique [implémentation des modèles de conception dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.Microsoft.com/fwlink/?) LinkId = 140042) dans la documentation de BizTalk Server et [modèles et meilleures pratiques pour l’intégration d’entreprise](http://go.microsoft.com/fwlink/?LinkId=140043) (http://go.Microsoft.com/fwlink/?) LinkId = 140043).  
  
## <a name="make-appropriate-use-of-net-classes-in-orchestrations-to-maximize-performance"></a>Faire un usage approprié de classes .NET dans les orchestrations pour optimiser les performances  
 En général, les classes .NET Framework utilisées à l’intérieur d’une orchestration peuvent être divisés en deux catégories distinctes :  
  
-   **Programmes d’assistance et des services -** ces classes fournissent des services communs aux orchestrations telles que le suivi, la gestion des erreurs, la mise en cache et la sérialisation/désérialisation. La plupart de ces classes peut être implémentée en tant que classes statiques avec aucun état interne et plusieurs méthodes statiques publiques. Cette approche évite la création de plusieurs objets de la même classe dans les différentes orchestrations en cours d’exécution en même temps, ce qui permet de réduire l’espace de travail de processus hôte et d’économiser de la mémoire. Une classe qui est sans état permet de réduire la taille globale de l’état interne qui doit être sérialisé et rendues persistantes dans la BizTalk MessageBox si une orchestration est en attente.  
  
-   **Entités et des objets métier -** vous pouvez utiliser ces classes pour gérer les entités, telles que des commandes, des éléments de commande et des clients. Une seule orchestration en interne, créez et gérer plusieurs instances du même type. Ces classes sont généralement avec état et exposent les champs publics et/ou propriétés ainsi que les méthodes pour modifier l’état interne de l’objet. Instances de ces classes peuvent être créés de façon dynamique par la désérialisation d’une partie de XLANGMessage dans un objet .NET à l’aide de la **XmlSerializer** ou **DataContractSerializer** classes ou à l’aide de la  **XLANGPart.RetrieveAs** (méthode). Vous devez structurer une orchestration en utilisant les étendues non transactionnel de sorte que les instances de classes avec état sont créées plus tard que possible et libérées dès qu’ils ne sont plus nécessaires. Cette approche permet de réduire l’espace de travail de processus hôte et réduit la taille globale de l’état interne qui est sérialisée et rendues persistantes dans la base de données MessageBox si une orchestration est en attente. Pour plus d’informations sur l’utilisation d’orchestrations dans BizTalk Server, consultez l’article [FAQ pour les Orchestrations BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=116886) (http://go.microsoft.com/fwlink/?LinkID=116886).  
  
    > [!NOTE]  
    >  Alors que cet article est écrit pour BizTalk Server 2004 et BizTalk Server 2006, les concepts présentés s’appliquent également aux orchestrations de BizTalk Server 2010.  
  
## <a name="orchestration-exception-handler-blocks"></a>Blocs de gestionnaire d’Exception d’orchestration  
 Lorsque vous utilisez des blocs de gestionnaire d’exception d’Orchestration, incluent toutes les formes d’orchestration dans une ou plusieurs étendues (non transactionnels étendues autant que possible) et créer au moins les blocs de gestionnaire d’exception suivants :  
  
-   Un bloc de gestionnaire d’exceptions pour la gestion d’une erreur générique de System.Exception.  
  
-   Un bloc de gestionnaire d’exceptions pour gérer une exception générale afin d’intercepter et gérer les erreurs possibles non managées, telles que les exceptions COM.  
  
 Pour plus d’informations sur l’utilisation des blocs d’exceptions d’Orchestration, consultez les articles suivants :  
  
-   [À l’aide de la gestion des exceptions de BizTalk Server](http://msdn.microsoft.com/library/aa561229.aspx) (http://msdn.microsoft.com/library/aa561229.aspx).  
  
-   [Blog de Charles Young, BizTalk Server 2006 : Le modèle de Compensation](http://go.microsoft.com/fwlink/?LinkId=158017) (http://go.microsoft.com/fwlink/?LinkId=158017).  
  
    > [!NOTE]  
    >  Pendant ce billet de blog a été écrit avec [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] à l’esprit les principes décrits dans le blog s’appliquent également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="considerations-when-using-maps-in-orchestrations"></a>Considérations sur l’utilisation de mappages dans les orchestrations  
 Les considérations suivantes s’appliquent lors de l’utilisation de mappages dans les orchestrations :  
  
-   Si vous utilisez une carte à extraire ou définir les propriétés utilisées avec la logique métier dans une orchestration, utilisez les champs distinctifs ou des propriétés promues. Cette pratique doit être suivie, car lorsque extraction ou de la définition des valeurs avec une carte du document est chargé en mémoire toutefois lorsque des champs distinctifs ou les propriétés promues, le moteur d’orchestration accède au contexte du message et ne charge pas le document en mémoire.  
  
-   Si vous utilisez un mappage pour regrouper plusieurs champs en un seul, utilisez des champs distinctifs ou des propriétés promues avec une variable d'orchestration pour obtenir le jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances](../technical-guides/optimizing-performance.md)