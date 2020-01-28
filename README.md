# wuhan2020-test

![Alt text](https://g.gravizo.com/source/custom_mark1?https%3A%2F%2Fraw.githubusercontent.com%wuhan2020%wuhan2020-test%2Fmaster%2FREADME.md)
<details> 
<summary></summary>
custom_mark1

@startuml
!includeurl https://raw.githubusercontent.com/RicardoNiepel/C4-PlantUML/master/C4_Container.puml

'LAYOUT_AS_SKETCH()

Person(volunteer, "志愿者")

System_Boundary(database,"数据集合"){
    System(shimo, "石墨", "excel表单集合")
    System(github, "wuhan2020/wuhan2020", "yaml文件集合")
}

System_Boundary(data, "wuhan2020/data-sync"){
    System(dataFetcher, "数据获取模块", "")
    System_Boundary(dataParser, "数据解析模块"){
        System_Ext(pluginYML, "YAML插件")
        System_Ext(pluginXML, "XML插件")
        System_Ext(pluginCVS, "CVS插件")
        System_Ext(pluginOther, "...")
    }
}

System_Boundary(web, "wuhan2020/web-server"){
    System(webAPI, "rest-API 服务器", "")
    System(webFront, "web前端展示", "")
}

Rel(volunteer, shimo, "填写表单")
Rel(shimo, dataFetcher, "原始数据获取")
Rel(dataFetcher, pluginYML,"数据解析")
Rel(dataFetcher, pluginXML,"数据解析")
Rel(dataFetcher, pluginCVS,"数据解析")
Rel(dataFetcher, pluginOther,"数据解析")
Rel(pluginYML, github, "yaml文件更新")
Rel(webAPI, github, "获取数据")
Rel(webFront, webAPI, "渲染页面")
@enduml

custom_mark1
</details>
