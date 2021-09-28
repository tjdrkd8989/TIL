## `config`

* 기본 에디터 : `vim` => visual studio code로 변경

```bash
$ git config --global core.editor "code --wait"
```

## `.gitignore`

> git으로 관리하지 않을 파일 목록

```bash
# 특정 파일
data.csv
# 특정 폴더
secret/
# 특정 확장자 (*)
*.csv
```

* 일반적인 개발 환경에서 필수적으로 등록하는 예시

  * OS, IDE(eclipse) / Text editor(vs code), 특정 언어나 프레임워크에서 생성되는 파일 

    * ex) 임시파일/실행을 위해서 필요한 파일

    * https://github.com/github/gitignore/blob/master/Java.gitignore

    * https://gitignore.io/ 

      * 예시) `windows`, `java`, `eclipese`

      ```bash
      # Created by https://www.toptal.com/developers/gitignore/api/windows,java,eclipse
      # Edit at https://www.toptal.com/developers/gitignore?templates=windows,java,eclipse
      
      ### Eclipse ###
      .metadata
      bin/
      tmp/
      *.tmp
      *.bak
      *.swp
      *~.nib
      local.properties
      .settings/
      .loadpath
      .recommenders
      
      # External tool builders
      .externalToolBuilders/
      
      # Locally stored "Eclipse launch configurations"
      *.launch
      
      # PyDev specific (Python IDE for Eclipse)
      *.pydevproject
      
      # CDT-specific (C/C++ Development Tooling)
      .cproject
      
      # CDT- autotools
      .autotools
      
      # Java annotation processor (APT)
      .factorypath
      
      # PDT-specific (PHP Development Tools)
      .buildpath
      
      # sbteclipse plugin
      .target
      
      # Tern plugin
      .tern-project
      
      # TeXlipse plugin
      .texlipse
      
      # STS (Spring Tool Suite)
      .springBeans
      
      # Code Recommenders
      .recommenders/
      
      # Annotation Processing
      .apt_generated/
      .apt_generated_test/
      
      # Scala IDE specific (Scala & Java development for Eclipse)
      .cache-main
      .scala_dependencies
      .worksheet
      
      # Uncomment this line if you wish to ignore the project description file.
      # Typically, this file would be tracked if it contains build/dependency configurations:
      #.project
      
      ### Eclipse Patch ###
      # Spring Boot Tooling
      .sts4-cache/
      
      ### Java ###
      # Compiled class file
      *.class
      
      # Log file
      *.log
      
      # BlueJ files
      *.ctxt
      
      # Mobile Tools for Java (J2ME)
      .mtj.tmp/
      
      # Package Files #
      *.jar
      *.war
      *.nar
      *.ear
      *.zip
      *.tar.gz
      *.rar
      
      # virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
      hs_err_pid*
      
      ### Windows ###
      # Windows thumbnail cache files
      Thumbs.db
      Thumbs.db:encryptable
      ehthumbs.db
      ehthumbs_vista.db
      
      # Dump file
      *.stackdump
      
      # Folder config file
      [Dd]esktop.ini
      
      # Recycle Bin used on file shares
      $RECYCLE.BIN/
      
      # Windows Installer files
      *.cab
      *.msi
      *.msix
      *.msm
      *.msp
      
      # Windows shortcuts
      *.lnk
      
      # End of https://www.toptal.com/developers/gitignore/api/windows,java,eclipse
      ```

      

      # push error

      ## 에러 상황

      ```bash
      $ git push origin master
      To https://github.com/edutak/0928.git
       ! [rejected]        master -> master (fetch first)
      error: failed to push some refs to 'https://github.com/edutak/0928.git'
      # Updates 거절.
      # 원격저장소 작업이 로컬에 없어서 
      hint: Updates were rejected because the remote contains work that you do
      hint: not have locally. This is usually caused by another repository pushing
      # 다시 push하기 전에, 원격저장소 변경사항들을 먼저 통합하는 것을 원할 것..
      hint: to the same ref. You may want to first integrate the remote changes
      hint: (e.g., 'git pull ...') before pushing again.
      hint: See the 'Note about fast-forwards' in 'git push --help' for details.
      
      ```

      ## 해결

      ### 1. pull

      ```bash
      $ git pull origin master
      remote: Enumerating objects: 4, done.
      remote: Counting objects: 100% (4/4), done.
      remote: Compressing objects: 100% (3/3), done.
      remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
      Unpacking objects: 100% (3/3), 2.04 KiB | 208.00 KiB/s, done.
      From https://github.com/edutak/0928
       * branch            master     -> FETCH_HEAD
         2a71213..c143740  master     -> origin/master
      hint: Waiting for your editor to close the fiMerge made by the 'recursive' strategy.
       22.md | 159 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
       1 file changed, 159 insertions(+)
       create mode 100644 22.md
      
      ```

      * 커밋 메시지(merge)가 발생

        ```bash
        $ git log --oneline
        9f0d621 (HEAD -> master) Merge branch 'master' of https://github.com/edutak/0928
        772310c Add d.txt
        c143740 (origin/master) Add files via upload
        2a71213 Update
        
        ```

        

      * 충돌 발생시 해결이 필요

      ### 2. push

      ```bash
      $ git push origin master
      Enumerating objects: 6, done.
      Counting objects: 100% (6/6), done.
      Delta compression using up to 12 threads
      Compressing objects: 100% (4/4), done.
      Writing objects: 100% (4/4), 482 bytes | 482.00 KiB/s, done.
      Total 4 (delta 2), reused 0 (delta 0), pack-reused 0
      remote: Resolving deltas: 100% (2/2), completed with 1 local object.
      To https://github.com/edutak/0928.git
         c143740..9f0d621  master -> master
      ```

      

      