# Stack-dockerbuild

Service catalog Docker Build stack

Build and test a docker image before pushing it to a registry

# Requirements

In order to run this task, couple elements are required within the infrastructure:

  * Having a registry to store the builded Docker image

# Details

## Pipeline

<img src="docs/pipeline.png" width="800">

**Jobs description**

  * `build`: Composed of several steps that you can provide : test, build, post build tests, upload the image.

Those steps can be configured for your own usage by putting the file from `docker/.ci/` into a `.ci` directory in your Docker image git repository `build.yml`, `post-tests.yml` and `tests.yml`.

**Params**

|Name|Description|Type|Default|Required|
|---|---|:---:|:---:|:---:|
|`code_build_context`|Path from the repository root to the files to build. The Dockerfile location is relative to this path.|`-`|`.`|`True`|
|`code_build_env`|Environment variable of the build task.|`-`|``|`False`|
|`code_dockerfile_location`|Dockerfile location related to code_build_context|`-`|`Dockerfile`|`True`|
|`code_git_branch`|Branch of the code git repository.|`-`|`master`|`True`|
|`code_git_private_key`|SSH key pair to fetch the code git repository.|`-`|`((git_code.ssh_key))`|`True`|
|`code_git_repository`|Git repository url containing the code of the stack.|`-`|`git@github.com:MyUser/code-magento.git`|`True`|
|`customer`|Name of the Cycloid Organization, used as customer variable name.|`-`|`($ organization_canonical $)`|`True`|
|`env`|Name of the project's environment.|`-`|`($ environment $)`|`True`|
|`project`|Name of the project.|`-`|`($ project $)`|`True`|
|`registry_extra_tags`|Additional tags to put on the builded image.|`-`|``|`False`|
|`registry_image_name`|Name of the repository image.|`-`|`myuser/imagename`|`True`|
|`registry_password`|Password of image repository.|`-`|`secret`|`True`|
|`registry_tag`|tag to put on the builded image.|`-`|`latest`|`True`|
|`registry_tag_commit_id`|Add additionnal tag using short commit id|`bool`|`false`|`False`|
|`registry_username`|Username of image repository.|`-`|`myuser`|`True`|
|`stack_git_branch`|Branch to use on the public stack git repository|`-`|`master`|`True`|

