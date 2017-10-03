---
title: "Comment déployer un adaptateur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f17b336c-6232-4889-ab7e-92b83fab0f5f
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e36443b99f01688a38e66a4a302ab64bb220092f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-custom-adapter"></a>Déploiement d'un adaptateur personnalisé
Le processus complet d'installation d'un adaptateur est constitué des étapes suivantes :  
  
1.  Vérifiez les dépendances. Par exemple, le programme d'installation de l'adaptateur MSMQ vérifie l'existence du service MSMQ local car le composant d'exécution de l'adaptateur en dépend.  
  
2.  Configurez le système de fichiers local. Cela comprend la création de dossiers d'installation et la copie de fichiers binaire et de prises en charge. Assurez-vous que l'accès aux dossiers et les autorisations d'accès aux fichiers sont configurés correctement.  
  
3.  Installez des assemblys managés dans le Global Assembly Cache du système.  
  
4.  Créez des clés de registre pour l'adaptateur.  
  
    > [!NOTE]
    >  Pour un adaptateur 32 bits, la console Administration de BizTalk Server utilise la branche HKEY_CLASSES_ROOT du registre pour obtenir la configuration personnalisée de l'adaptateur.  Si un adaptateur 32 bits est installé sur un serveur 64 bits, la console Administration de BizTalk Server utilise alors la branche HKEY_CLASSES_ROOT\Wow6432Node\ pour les données de configuration de l'adaptateur.  
  
5.  Ajoutez l'adaptateur à BizTalk Server. Cela signifie que de nouvelles entrées de la base de données de gestion BizTalk pour l'adaptateur ainsi que pour le schéma de propriété sont utilisées pour refléter les propriétés promues par l'adaptateur. Cette étape est parfois effectuée manuellement à l'aide de la console Administration de BizTalk Server.  
  
## <a name="exceptions"></a>Exceptions  
 Le programme d'installation de l'adaptateur ne doit pas obligatoirement vérifier les dépendances pour les installations partielles de BizTalk Server. Par exemple, pour une installation des outils d'administration uniquement, le programme d'installation de l'adaptateur n'est pas obligé de vérifier les dépendances du composant d'exécution de l'adaptateur car celui-ci n'est pas utilisé. Cela est également valable pour une installation du composant d'exécution BizTalk Server uniquement, pour laquelle le programme d'installation de l'adaptateur n'est pas obligé de vérifier les dépendances du composant de conception de l'adaptateur.  
  
 Dans les environnements BizTalk Server multi-serveurs, la dernière étape de la liste précédente (Ajout de l'adaptateur à BizTalk Server) se produit uniquement lors de l'installation de l'adaptateur sur le premier serveur BizTalk Server. Cela est dû au fait que toutes les instances de service BizTalk Server  partagent la même base de données de gestion BizTalk (dotée du nom par défaut BizTalkMgmtDB). Si des adaptateurs sont ajoutés à d'autres serveurs BizTalk du même groupe, les étapes suivantes échouent.  
  
## <a name="install-the-adapter-assemblies-into-the-global-assembly-cache"></a>Installez les assemblys de l'adaptateur dans le Global Assembly Cache.  
 Pour une prise en charge de plusieurs environnements hôtes BizTalk Server avec différents chemins d'installation pour les adaptateurs, les assemblys d'adaptateur doivent être installés dans le Global Assembly Cache du système.  
  
 Lors de l'installation et de la configuration de l'adaptateur, une nouvelle entrée d'adaptateur est créée dans la table adm_adapter de la base de données de gestion BizTalk (dotée du nom par défaut BizTalkMgmtDB). Cette entrée contient toutes les données de référence utilisées par BizTalk Server pour le composant d'exécution et le composant de conception.  
  
 Le **InBoundAssemblyPath** et **OutboundAssemblyPath** champs sont utilisés par l’exécution de BizTalk Server pour savoir où charger les binaires de l’adaptateur. Étant donné qu'il n'y a qu'une base de données de gestion BizTalk par groupe BizTalk Server, tous les serveurs BizTalk du groupe doivent partager ces données. Si vous voulez installer l'adaptateur sur différents serveurs BizTalk au sein du groupe, vous devez utiliser le même chemin d'installation sur chacun des serveurs. Si le chemin d'installation local est différent du chemin stocké dans la base de données de gestion BizTalk, le serveur BizTalk Server ne peut pas charger les binaires de l'adaptateur.  
  
 Signez toujours l'assembly de l'adaptateur avec un nom fort et utilisez Gacutil.exe pour placer l'assembly de l'adaptateur dans le Global Assembly Cache du système lors de l'installation de l'adaptateur. Assurez-vous que vous laissez le **InBoundAssemblyPath** et **OutboundAssemblyPath** champs null ou vides.  
  
## <a name="using-the-framework-for-adapter-configuration"></a>Utilisation de l'infrastructure de configuration de l'adaptateur  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit une méthode permettant de générer des feuilles de propriétés pour l'interface utilisateur de configuration de l'adaptateur. Ce mécanisme est basé sur une définition XSD (XML Schema Definition) des propriétés de configuration. L'utilisation de cette infrastructure présente des défis importants au développeur de l'adaptateur. Cette section suggère une solution efficace à certains de ces problèmes.  
  
### <a name="consider-custom-property-editors-for-all-your-key-properties"></a>Envisagez d'utiliser des éditeurs de propriétés personnalisées pour toutes vos principales propriétés.  
 Il est impossible d'appliquer une validation de propriété significative à des propriétés de la feuille de propriétés. L'infrastructure tente d'utiliser des restrictions simpletype XSD (XML Schema Definition) pour définir les règles de validation pour l'interface utilisateur. Les règles simples pour les valeurs maximum et minimum sont appliquées mais la restriction d'expression régulière pour les champs de type chaîne n'est pas prise en charge. En outre, les données sont converties en types CLR (Common Language Runtime) avant l'application de la restriction. Cela signifie que l'utilisateur de l'interface obtient parfois un message d'erreur énigmatique relatif à la conversion de type plutôt qu'un message d'erreur relatif à une valeur hors limite. Tout compte fait, la logique de validation est ténue.  
  
 La solution adoptée par de nombreux développeurs consiste à développer des éditeurs de propriétés personnalisées pour les propriétés principales de leur feuille de propriétés. S'il existe plusieurs propriétés dépendantes les unes des autres, (ce qui est souvent le cas), l'éditeur de propriétés personnalisées peut combiner les résultats dans un seul champ et le composant d'exécution peut les séparer ultérieurement. Cette méthode est la seule qui permet d'insérer le code personnalisé obligatoire (bien qu'insignifiant) dans l'interface.  
  
 Les éditeurs de propriétés personnalisées sont relativement faciles à développer et la propriété de la définition XSD peut être annotée pour faciliter leur utilisation. L'annotation fait référence à un assembly qui expose le point d'entrée de l'éditeur de propriété. En outre, elle est codée pour afficher un formulaire CLR. Vous pouvez maintenant développer une interface utilisateur normale et utiliser les outils de génération d'interface traditionnels proposés par Visual Studio.  
  
 L'exemple de code suivant illustre l'utilisation de la définition XSD pour ajouter un éditeur de propriétés personnalisées :  
  
```  
<xs:element name="queueDetails" type="xs:string" minOccurs="0">  
    <xs:annotation>  
        <xs:appinfo>  
           <baf:designer>  
               <baf:displayname _locID="queueName">Queue Definition</baf:displayname>  
               <baf:description _locID="receiveQueueDesc">Details of MQSeries Server, Queue Manager and Queue from where you want to receive messages.</baf:description>  
               <baf:category _locID="mqsCategory">MQSeries</baf:category>  
               <baf:editor assembly="Microsoft.BizTalk Server.Adapter.MQSAdmin.dll">Microsoft.BizTalk Server.Adapter.MQSAdmin.MQSUITypeEditor</baf:editor>  
            </baf:designer>  
        </xs:appinfo>  
    </xs:annotation>  
</xs:element>  
  
```  
  
 Le code référencé doit se présenter comme suit :  
  
```  
public class MQSUITypeEditor : System.Drawing.Design.UITypeEditor  
{  
public override System.Drawing.Design.UITypeEditorEditStyle GetEditStyle  
(System.ComponentModel.ITypeDescriptorContext context)   
{  
return System.Drawing.Design.UITypeEditorEditStyle.Modal;  
}  
public override object EditValue (System.ComponentModel.ITypeDescriptorContext context,  
System.IServiceProvider provider, object value)   
{  
Form qdForm = new QueueDefinitionForm(value);  
IWindowsFormsEditorService service =   
(IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));  
DialogResult dialogResult = service.ShowDialog(qdForm);  
//…  
}  
}  
class QueueDefinitionForm : System.Windows.Forms.Form   
{  
//  traditional UI code goes here!  
}  
  
```  
  
 Le composant d'administration doit être en mesure de trouver l'assembly référencé dans la définition XSD. Vous devez donc l'ajouter au Global Assembly Cache.