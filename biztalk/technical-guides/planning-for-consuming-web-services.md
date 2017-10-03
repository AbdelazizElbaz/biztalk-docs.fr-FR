---
title: "Planification de l’utilisation de Services Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24863069-929b-4b0b-9643-073965fb5532
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a13151a5dd76b20b70872b963dc6a688370444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-consuming-web-services"></a>Planification de la consommation de Services Web
Planification des services Web peut être divisé en deux catégories, la planification de la publication de services Web et de planification pour la consommation de services Web. Cette rubrique décrit les considérations pour l’utilisation de services Web. Pour plus d’informations sur la publication de services Web, consultez [planification de publication Web Services1](../technical-guides/planning-for-publishing-web-services1.md).  
  
 Gardez les éléments suivants à l’esprit que vous créez votre plan de :  
  
-   **À l’aide de deux traits de soulignement dans un nom de paramètre**  
  
     Les noms de paramètres de méthodes Web ne peuvent pas commencer par « __ » (deux caractères de soulignement). Les noms commençant ainsi peuvent créer des parties de message Web non prises en charge (inutilisables) par XLANG/s.  
  
-   **L’élément Any et l’anyAttribute sont pas pris en charge dans les méthodes Web**  
  
     Vous ne pouvez pas utiliser le **tout** élément ou **anyAttribute** attribut dans le schéma pour une méthode Web.  
  
-   **À l’aide de mots clés XLANG/s**  
  
     Un nom de service ou de méthode Web ne peut pas être un mot clé XLANG/s. Si vous utilisez un mot clé XLANG/s dans le nom de service ou de méthode Web, vous obtenez une erreur de compilation lorsque vous ajoutez le service Web. Pour obtenir la liste de mots réservés pour le langage XLANG/s, consultez le [les mots réservés XLANG/s](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).  
  
-   **Prise en charge XLANG/s requis pour les Types de paramètre**  
  
     À l’aide des types de paramètre de méthode XLANG/s pris en charge Web génère des erreurs de compilation. Par exemple, BizTalk Server ne prend pas en charge un paramètre composé d'un tableau unidimensionnel de types de schémas. En outre, BizTalk Server ne prend pas en charge les tableaux multidimensionnels. Pour obtenir la liste de mots en langage XLANG/s se réserve dans BizTalk Server, consultez [les mots réservés XLANG/s](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).  
  
-   **Comment éviter les erreurs de Compilation générées par l’ajout de mots clés c# contenant ou des identificateurs de références Web**  
  
     Lorsque vous utilisez la **ajouter une référence Web**pour ajouter des références Web aux projets BizTalk, BizTalk Server convertit les types de schémas qui sont requises pour appeler chaque méthode Web aux schémas. BizTalk Server ajoute ces schémas à Reference.xsd. Si vos schémas contiennent des noms d'élément qui sont des mots clés C# ou que le nom d'élément n'est pas valide en tant qu'identificateur C#, vous risquez d'obtenir une erreur d'exécution. Pour éviter ces erreurs, assurez-vous que le service Web utilisé ne contient pas de noms d'élément qui sont des mots clés C# ou des identificateurs C# non valides.  
  
-   **Plusieurs définitions de Type de Service/Port sont pris en charge**  
  
     BizTalk Server prend en charge l'ajout d'un fichier de service Web avec une définition unique de service et de type de port. Si vous ajoutez un fichier WSDL avec plusieurs définitions de service ou de type de port, vous risquez d'obtenir l'erreur suivante :  
  
     `Could not generate BizTalk files. Object reference not set to an instance of an object.`  
  
-   **Prise en charge de l’utilisation de tableaux exposés par les Services Web**  
  
     BizTalk Server peut utiliser un tableaux et en escalier exposés par les services Web qui ne sont pas des services Web BizTalk Server. Pour plus d’informations sur l’utilisation des tableaux de service Web, consultez [comment consommer des tableaux de Service Web](http://go.microsoft.com/fwlink/?LinkId=155766) (http://go.microsoft.com/fwlink/?LinkId=155766).  
  
    > [!NOTE]  
    >  La syntaxe de tableau multidimensionnel n'est pas prise en charge Par exemple, *MyArray [1,5]*.  
  
    > [!NOTE]  
    >  BizTalk Server ne prend pas en charge l’utilisation d’un tableau de **DataSet** objets exposés par un service Web. Le sous-service XLANG/s prend en charge la classe .NET DataSet, mais si vous créez un projet BizTalk qui contient une référence Web à un service Web qui expose un tableau d’objets .NET DataSet vous obtenez des erreurs lorsque vous essayez de compiler le projet.  
  
-   **Paramètres de méthode Web doivent être sérialisables Xml.**  
  
     Tous les paramètres dans un service Web utilisé doivent pouvoir faire l'objet d'une sérialisation XML. Si vous ajoutez une méthode Web qui contient un paramètre non sérialisable XML, vous risquez de recevoir le message d'erreur suivant :  
  
     System.Xml.Element doit être sérialisable XML pour être un type de partie de message.  
  
    > [!NOTE]  
    >  Les types de données, **XmlDocument** et **DataSet**, pourtant non sérialisables Xml, sont pris en charge.  
  
-   **Utilisation de Services Web messagerie seule**  
  
     Lors de l’utilisation des services Web messagerie seule, tous les noms de corps de message BizTalk Server doivent correspondre les noms de paramètres de méthode Web. Par exemple, si la signature du service Web est `WebMethod(MyType1 type1, MyType2 type2)` et que le nom de la partie doit être type1 et type2, vous risquez d'obtenir l'erreur d'exécution suivante :  
  
     `Failed to retrieve the message part for parameter %1`  
  
     Pour plus d’informations, consultez [comment consommer des Services Web dans un scénario de Messaging-Only](http://go.microsoft.com/fwlink/?LinkId=155767) (http://go.microsoft.com/fwlink/?LinkId=155767).  
  
-   **Configuration d’un Port d’envoi SOAP par programme**  
  
     Il est possible de définir les propriétés de configuration par programme dans le contexte de message. Si le port d’envoi est statique ou dynamique, vous pouvez définir ces propriétés dans une orchestration ou un composant de pipeline personnalisé.  
  
    > [!NOTE]  
    >  Pour configurer le **MethodName** propriété le protocole SOAP statique de port d’envoi par programme, vous devez définir **nom de la méthode** à **[spécifier plus tard]** dans le **Web Service** onglet de la **propriétés du Transport SOAP** boîte de dialogue dans la console Administration de BizTalk Server.  
  
     Pour plus d’informations sur la **MethodName** propriété, consultez [comment définir de façon dynamique l’URI d’un Service Web consommé](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).  
  
-   **Règles de propriété**  
  
     Si la propriété de configuration est définie dans une orchestration ou un composant de pipeline personnalisé dans un pipeline de réception, alors les règles suivantes s'appliquent :  
  
    -   Si un message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.  
  
    -   Si un message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.  
  
     Si une propriété de configuration est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors la règle suivante s'applique :  
  
    -   La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique. En d'autres termes, les composants de pipeline d'envoi remplacent la propriété de configuration, quelle que soit l'origine de sa définition.  
  
    -   Pour plus d’informations sur les composants de pipeline personnalisés, consultez [développement des composants de Pipeline personnalisés](http://go.microsoft.com/fwlink/?LinkId=155769) (http://go.microsoft.com/fwlink/?LinkId=155769).  
  
    -   Pour plus d’informations sur les propriétés de configuration de l’adaptateur d’envoi SOAP, consultez [comment définir de façon dynamique l’URI d’un Service Web consommé](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).  
  
-   **Ajout d’une référence Web à un Service Web utilisé contenant un schéma à plusieurs racines provoque une erreur de Compilation**  
  
     Si vous ajoutez une référence Web à votre projet pour un service Web qui est dérivé d’une orchestration BizTalk publiée et que l’orchestration contient un schéma avec plusieurs racines, une erreur se produit lorsque le projet est compilé. Si vous ajoutez une référence Web à votre projet qui était dérivé d'une orchestration BizTalk publiée, assurez-vous que l'orchestration ne contient pas de schémas avec plusieurs racines.  
  
-   **Utilisation de TypedDataSets comme paramètres aux méthodes Web**  
  
     Pour prendre en charge l'utilisation de TypedDataSets comme paramètres de méthodes Web, procédez comme suit :  
  
    1.  Ajoutez la référence Web à un projet C#, puis générez le proxy.  
  
    2.  Créez un port d'envoi SOAP, spécifiez le proxy sur le port d'envoi, puis sélectionnez la méthode.  
  
    3.  Dans l'orchestration, définissez un port à liaison tardive et les types de messages. La plupart des cas où aucune promotion de propriétés ou l’accès au champ distinctif n’est nécessaire, le type peut être défini comme **XMLDocument**. Sélectionnez les pipelines PassThrough avec ce type.  
  
    4.  Dans la console Administration de BizTalk Server, dans le **Service Web** onglet dans le **propriétés du Transport SOAP** boîte de dialogue de SOAP port d’envoi, spécifiez que vous souhaitez utiliser le proxy que vous avez créé. Vous devez également spécifier l'assembly, le type et la méthode.  
  
-   **Ajout d’une référence Web à un Service Web utilisé contenant une méthode Web attendant des paramètres basés sur les génériques provoque une erreur de Compilation**  
  
     Si vous ajoutez une référence Web à votre projet pour un service Web qui contient une méthode Web attendant des paramètres tels que les paramètres de type nullable générique, une erreur se produit lorsque le projet est compilé. Cela n'est pas pris en charge. Vous devez utiliser une spécialisation explicite pour appeler la classe générique à partir de XLANG/s.  
  
-   **Génération de schéma BizTalk à l’aide de l’ajouter une référence Web**  
  
     Lorsque vous utilisez la **ajouter une référence Web**pour ajouter des références Web aux projets BizTalk, BizTalk Server convertit les types de schémas qui sont requises pour appeler chaque méthode Web aux schémas. BizTalk Server ajoute ces schémas à Reference.xsd. Pour vous assurer que le **ajouter une référence Web** génère les schémas BizTalk correctement, les services Web doivent respecter les consignes suivantes :  
  
    -   Méthodes Web doivent avoir **SoapDocumentMethodAttribute** au lieu de **SoapRpcMethodAttribute**.  
  
    -   Services Web et les méthodes doivent utiliser le **littéral** de liaison à la place de **Encoded** comme **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**.  
  
    -   Paramètres de méthode Web et retourner les types doivent avoir **XmlRootAttribute** avec valide **Namespace** propriété sauf s’ils sont des types XSD natifs et du type XmlNode.  
  
    -   Les méthodes Web ne doivent pas utiliser le **RequestNamespace** et **ResponseNamespace** propriétés dans **SoapDocumentMethodAttribute**.  
  
    -   Les services Web doivent être conformes à WS-I Basic Profile version 1.1.  
  
-   **L’ajouter une référence Web ne prend pas en charge l’élément d’importation de Web Services Description Language (WSDL)**  
  
     Ajouter une référence Web échoue lorsque vous ajoutez des références Web pour le fichier WSDL avec l’élément d’importation.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification du niveau BizTalk Server](../technical-guides/planning-the-biztalk-server-tier.md)