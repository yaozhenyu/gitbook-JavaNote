# 流程设计

一、 创建 Activiti Diagram，生成.bpmn文件

二、

```
private static ProcessEngine processEngine = ProcessEngines.getDefaultProcessEngine();
/**
 * 通过定义好的流程图文件部署，一次只能部署一个流程
 */
public static void deploy() {
    RepositoryService repositoryService = processEngine.getRepositoryService();
    Deployment deployment = repositoryService.createDeployment()
            .addClasspathResource("death/note/lawliet/web/workflow/leave.bpmn").deploy();
}
/**
 * 将多个流程文件打包部署，一次可以部署多个流程
 */
public void deployByZip() {
    InputStream is = this.getClass().getClassLoader().getResourceAsStream("diagrams/bpm.zip");
    ZipInputStream zip = new ZipInputStream(is);
    Deployment deployment = processEngine
            .getRepositoryService()
            .createDeployment()
            .addZipInputStream(zip)
            .deploy();
}
```



