---
title: "Considérations relatives à la consommation de Services Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea7038dc-4740-4c0a-b6a1-08bc22f42bc2
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c5cbef60d968119950b6c426a45c94d2e9ab60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-consuming-web-services"></a>Considérations à prendre en compte lors de l'utilisation de service Web
Cette section fournit des informations à prendre en considération lors de l'utilisation des services Web.  
  
## <a name="using-two-underscore-characters-in-a-parameter-name"></a>Utilisation de deux caractères de soulignement dans un nom de paramètre  
 Les noms de paramètres de méthodes Web ne peuvent pas commencer par « __ » (deux caractères de soulignement). Les noms commençant ainsi peuvent créer des parties de message Web non prises en charge (inutilisables) par XLANG/s.  
  
## <a name="the-any-element-and-the-anyattribute-attributes-are-not-supported-in-web-methods"></a>L'élément any et les attributs anyAttribute ne sont pas pris en charge dans les méthodes Web.  
 Vous ne pouvez pas utiliser le **tout** élément ou **anyAttribute** attribut dans le schéma pour une méthode Web.  
  
## <a name="using-xlangs-keywords"></a>Utilisation de mots clés XLANG/s  
 Un nom de service ou de méthode Web ne peut pas être un mot clé XLANG/s. Si vous utilisez un mot clé XLANG/s dans le nom de service ou de méthode Web, vous obtenez une erreur de compilation lorsque vous ajoutez le service Web. Pour obtenir la liste de mots réservés pour le langage XLANG/s, consultez [les mots réservés XLANG-s](../core/xlang-s-reserved-words.md).  
  
## <a name="required-xlangs-support-for-parameter-types"></a>Prise en charge par XLANG/s requise pour les types de paramètres  
 L'utilisation du type de paramètre de méthode Web non pris en charge par XLANG/s génère des erreurs de compilation. Par exemple, BizTalk Server ne prend pas en charge un paramètre composé d'un tableau unidimensionnel de types de schémas. En outre, BizTalk Server ne prend pas en charge les tableaux multidimensionnels. Pour obtenir la liste de mots en langage XLANG/s se réserve dans BizTalk Server, consultez [les mots réservés XLANG-s](../core/xlang-s-reserved-words.md).  
  
## <a name="avoiding-compilation-errors-caused-by-adding-web-references-containing-c-keywords-or-identifiers"></a>Prévention des erreurs de compilation générées par l'ajout de références Web contenant des mots clés ou identificateurs C#  
 Lorsque vous utilisez la **ajouter une référence de Service** pour ajouter des références de service aux projets BizTalk, BizTalk Server convertit les types de schémas qui sont requises pour appeler chaque méthode Web aux schémas. BizTalk Server ajoute ces schémas à Reference.xsd. Si vos schémas contiennent des noms d'élément qui sont des mots clés C# ou que le nom d'élément n'est pas valide en tant qu'identificateur C#, vous risquez d'obtenir une erreur d'exécution. Pour éviter ces erreurs, assurez-vous que le service Web utilisé ne contient pas de noms d'élément qui sont des mots clés C# ou des identificateurs C# non valides.  
  
## <a name="multiple-serviceport-type-definitions-are-unsupported"></a>Plusieurs définitions de service / type de port ne sont pas prises en charge.  
 BizTalk Server prend en charge l'ajout d'un fichier de service Web avec une définition unique de service et de type de port. Si vous ajoutez un fichier WSDL avec plusieurs définitions de service ou de type de port, vous risquez d'obtenir l'erreur suivante :  
  
 Impossible de générer les fichiers BizTalk. référence d'objet non définie sur une instance d'un objet.  
  
## <a name="support-for-consuming-arrays-exposed-by-web-services"></a>Prise en charge de l'utilisation de tableaux exposés par les services Web  
 BizTalk Server peut utiliser des tableaux unidirectionnels et en escalier exposés par les services Web autres que les services Web BizTalk. Pour plus d’informations sur l’utilisation des tableaux de service Web, consultez [comment consommer des tableaux de Service Web](../core/how-to-consume-web-service-arrays.md).  
  
> [!NOTE]
>  La syntaxe de tableau multidimensionnel n'est pas prise en charge Par exemple, `MyArray[1,5]`.  
  
> [!NOTE]
>  BizTalk Server ne prend pas en charge l’utilisation d’un tableau de **DataSet** objets exposés par un service Web. Le sous-service XLANG/s ne prend pas en charge de manière native la classe .NET DataSet, mais si vous créez un projet BizTalk contenant une référence Web à un service Web qui expose un tableau d'objets .NET DataSet, vous obtenez des erreurs lorsque vous tentez de compiler le projet.  
  
## <a name="web-method-parameters-must-be-xml-serializable"></a>Les paramètres de méthode Web doivent être sérialisables XML.  
 Tous les paramètres dans un service Web utilisé doivent pouvoir faire l'objet d'une sérialisation XML. Si vous ajoutez une méthode Web qui contient un paramètre non sérialisable XML, vous risquez de recevoir le message d'erreur suivant :  
  
 System.Xml.Element doit être sérialisable XML pour être un type de partie de message.  
  
> [!NOTE]
>  Les types de données, **XmlDocument** et **DataSet**, pourtant non sérialisables Xml, sont pris en charge.  
  
## <a name="consuming-messaging-only-web-services"></a>Utilisation de services Web messagerie seule  
 Lorsque vous utilisez les services Web messagerie seule, tous les noms de corps de messages BizTalk doivent correspondre aux noms de paramètres de méthode Web. Par exemple, si la signature du service Web est `WebMethod(MyType1 type1, MyType2 type2)` et que le nom de la partie doit être type1 et type2, vous risquez d'obtenir l'erreur d'exécution suivante :  
  
 Échec d'extraction de la partie du message du paramètre "%1".  
  
 Pour plus d’informations, consultez [comment consommer des Services Web dans un scénario de messagerie uniquement](../core/how-to-consume-web-services-in-a-messaging-only-scenario.md).  
  
## <a name="configuring-a-soap-send-port-programmatically"></a>Configuration d'un port d'envoi SOAP par programme  
 Il est possible de définir les propriétés de configuration par programme dans le contexte de message. Vous pouvez définir ces propriétés dans une orchestration ou un composant de pipeline personnalisé selon que le port d'envoi est statique ou dynamique.  
  
> [!NOTE]
>  Pour configurer le **MethodName** propriété le protocole SOAP statique de port d’envoi par programme, vous devez définir **nom de la méthode** à **[spécifier plus tard]** dans le **Web Service** onglet de la **propriétés du Transport SOAP** boîte de dialogue de la Console Administration de BizTalk Server.  
>   
>  Pour plus d’informations sur la **MethodName** propriété, consultez [comment définir de façon dynamique l’URI d’un Service Web consommé](../core/how-to-dynamically-set-the-uri-of-a-consumed-web-service.md).  
>   
>  Pour plus d’informations sur **propriétés du Transport SOAP** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport SOAP, service Web** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="property-rules"></a>Règles de propriété  
 Si la propriété de configuration est définie dans une orchestration ou un composant de pipeline personnalisé dans un pipeline de réception, alors les règles suivantes s'appliquent :  
  
-   Si un message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.  
  
-   Si un message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.  
  
 Si une propriété de configuration est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors la règle suivante s'applique :  
  
-   La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique. En d'autres termes, les composants de pipeline d'envoi remplacent la propriété de configuration, quelle que soit l'origine de sa définition.  
  
-   Pour plus d’informations sur les composants de pipeline personnalisés, consultez [développement des composants de Pipeline personnalisés](../core/developing-custom-pipeline-components.md).  
  
-   Pour plus d’informations sur les propriétés de configuration de l’adaptateur d’envoi SOAP, consultez [comment définir de façon dynamique l’URI d’un Service Web consommé](../core/how-to-dynamically-set-the-uri-of-a-consumed-web-service.md).  
  
## <a name="adding-a-web-reference-to-a-consumed-web-service-that-contains-a-multi-rooted-schema-will-cause-a-compilation-error"></a>L'ajout d'une référence Web à un service Web utilisé contenant un schéma à plusieurs racines peut générer une erreur de compilation.  
 Si vous ajoutez une référence Web à votre projet pour un service Web dérivé d'une orchestration BizTalk publiée et que l'orchestration contient un schéma avec plusieurs racines, une erreur est générée lors de la compilation du projet. Si vous ajoutez une référence Web à votre projet qui était dérivé d'une orchestration BizTalk publiée, assurez-vous que l'orchestration ne contient pas de schémas avec plusieurs racines.  
  
## <a name="using-typeddatasets-as-parameters-to-web-methods"></a>Utilisation de TypedDataSets comme paramètres de méthodes Web  
 Pour prendre en charge l'utilisation de TypedDataSets comme paramètres de méthodes Web, procédez comme suit :  
  
1.  Ajoutez la référence Web à un projet C#, puis générez le proxy.  
  
2.  Créez un port d'envoi SOAP, spécifiez le proxy sur le port d'envoi, puis sélectionnez la méthode.  
  
3.  Dans l'orchestration, définissez un port à liaison tardive et les types de messages. La plupart des cas où aucune promotion de propriétés ou l’accès au champ distinctif n’est nécessaire, le type peut être défini comme **XMLDocument**. Sélectionnez les pipelines PassThrough avec ce type.  
  
4.  Dans la console Administration de BizTalk Server, dans le **Service Web** onglet dans le **propriétés du Transport SOAP** boîte de dialogue de SOAP port d’envoi, spécifiez que vous souhaitez utiliser le proxy que vous avez créé. Vous devez également spécifier l'assembly, le type et la méthode. Pour plus d’informations, consultez la **boîte dialogue de propriétés du Transport SOAP, service Web** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="adding-a-web-reference-to-a-consumed-web-service-that-contains-a-web-method-expecting-generic-based-parameters-will-cause-a-compilation-error"></a>L'ajout d'une référence Web à un service Web utilisé contenant une méthode Web attendant des paramètres basés sur des génériques peut générer une erreur de compilation.  
 Si vous ajoutez une référence Web à votre projet pour un service Web qui contient une méthode Web attendant des paramètres basés sur des génériques, tels que des paramètres de type nullable, une erreur est générée lors de la compilation du projet. Cela n'est pas pris en charge. Vous devez utiliser une spécialisation explicite pour appeler la classe générique à partir de XLANG/s.  
  
## <a name="biztalk-schema-generation-using-the-add-service-reference"></a>Génération de schéma BizTalk à l'aide d'Ajouter une référence de service  
 Lorsque vous utilisez la **ajouter une référence de Service** pour ajouter des références de service aux projets BizTalk, BizTalk Server convertit les types de schémas qui sont requises pour appeler chaque méthode Web aux schémas. BizTalk Server ajoute ces schémas à Reference.xsd. Pour vous assurer que le **ajouter une référence de Service** génère les schémas BizTalk correctement, les services Web doivent respecter les consignes suivantes :  
  
-   Méthodes Web doivent avoir **SoapDocumentMethodAttribute** au lieu de **SoapRpcMethodAttribute**.  
  
-   Services Web et les méthodes doivent utiliser le **littéral** de liaison à la place de **Encoded** comme **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**.  
  
-   Paramètres de méthode Web et retourner les types doivent avoir **XmlRootAttribute** avec valide **Namespace** propriété sauf s’ils sont des types XSD natifs et du type XmlNode.  
  
-   Les méthodes Web ne doivent pas utiliser le **RequestNamespace** et **ResponseNamespace** propriétés dans **SoapDocumentMethodAttribute**.  
  
-   Les services Web doivent être conformes à WS-I Basic Profile version 1.1.  
  
## <a name="xsd-will-not-contain-nodes-for-simple-parameter-types"></a>XSD ne contient pas de nœuds pour les types de paramètres simples.  
 Lorsque vous ajoutez une référence Web et que la méthode Web a un paramètre qui est un type simple, le XSD généré ne contient pas de nœuds pour ce paramètre. Par contre, le message à parties multiples généré contient une partie de type simple. L'orchestration doit gérer convenablement cette partie de message. S'il s'agit d'une partie de la demande adressée au service Web, attribuez manuellement la valeur à cette partie avec une forme Assignation de message. S'il s'agit d'une partie de la réponse du service Web, accédez manuellement à cette partie dans une forme Expression pour voir la valeur.  
  
## <a name="the-add-service-reference-do-not-support-the-web-services-description-language-wsdl-import-element"></a>Ajouter une référence de service ne prend pas en charge l'élément d'importation WSDL (Web Services Description Language).  
 Ajouter une référence de service échoue lorsque vous ajoutez des références de service pour le fichier WSDL avec l'élément d'importation.  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de Messages Web](../core/constructing-web-messages.md)