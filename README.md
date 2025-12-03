<html>
    <head>
        <style>
            hr.c2
            {
                height:5px;
                background-image: linear-gradient(to right,green,cyan);
            }
            div#head
            {
                width:100%;
                height:50px;
                border: hidden;
                background-image: linear-gradient(to right,#0f0,#0ff);
                box-sizing:border-box;
                position: sticky;
                top:0;
            }
            #head h1
            {
                font-family: 'Brush Script MT', cursive;
                text-align: center;
            }
            div#menu
            {
                width:300px;
                height:150px;
                border: double;
                box-sizing: border-box;
            }
            div#login_post
            {
                width:300px;
                height:800px;
                border: double;
                box-sizing: border-box;
                display: none;
            }
            #login_post button
            {
                width:100%;
                height:100px;
            }
            div#login
            {
                width:300px;
                height:400px;
                border:double;
                box-sizing: border-box;
                display: none;
            }
            div#main
            {
                width:300px;
                height:800px;
                border: double;
                box-sizing: border-box;
                display: none;
            }
            #main button
            {
                width: 100%;
                height: 100px;
            }
            div#forum
            {
                display: none;
            }
            #forum div
            {
                width:100%;
                height:75px;
                border: hidden;
                background-color:hsla(216,100%,50%,0.5);
                box-sizing:border-box;
                position: sticky;
                top:0;
            }
            div#to_do_list
            {
                display: none;
            }
            #to_do_list div
            {
                width:100%;
                height:75px;
                border: hidden;
                background-image:linear-gradient(to right,hsla(180,100%,50%,0.5),hsla(270,100%,50%,0.5));
                box-sizing: border-box;
                position: sticky;
                top:0;
            }
            div#notebook
            {
                display: none;
            }
            #notebook div
            {
                width:100%;
                height:75px;
                border: hidden;
                background-image: linear-gradient(45deg, red, orange, yellow, green);
                box-sizing: border-box;
                position: sticky;
                top:0;
            }
            div#assignment
            {
                display:none;
            }
            #assignment div
            {
                width:100%;
                height:75px;
                border: hidden;
                background-image: linear-gradient(45deg, green, cyan, blue, purple);
                box-sizing: border-box;
                position: sticky;
                top:0;
            }
        </style>
    </head>
    <body>
        <div id="head">
            <h1>
                E-Campus
            </h1>
        </div>
        <div id="menu">
            <button type="button" onclick="user_post()">
                login
            </button>
            <br><br>
            <a href="https://github.com/UnKnown-cL/UnKnown-cL.github.io">
                >>>source_code<<<
            </a>
        </div>
        <div id="login_post">
            <p>
                choose a post
            </p>
            <hr class="c2">
            <button type="button" onclick="login_post('student')">
                student
            </button>
            <hr>
            <button type="button" onclick="login_post('teacher')">
                teacher
            </button>
            <button type="button" onclick="login_post('class teacher')">
                class teacher
            </button>
            <hr>
            <button type="button" onclick="login_post('owner')">
                principal(owner)
            </button>
        </div>
        <div id="login">
            <p id="form"/>
        </div>
        <div id="main">
            <p id="greeting"/>
            <hr class="c2">
            <button type="button" onclick="redirect('forum')">
                forum
            </button>
            <hr>
            <button type="button" onclick="redirect('to_do_list')">
                to_do_list
            </button>
            <button type="button" onclick="redirect('notebook')">
                notebook
            </button>
            <hr class="c2">
            <button type="button" onclick="sign_out()">
                sign out
            </button>
        </div>
        <div id="forum">
            <div>
                <input id="forum_input" value="type something here"/>
                <button type="button" onclick="forum_post()">
                    post
                </button>
                <button type="button" onclick="main()">
                    back
                </button>
            </div>
            <p id="forum_text"/>
        </div>
        <div id="to_do_list">
            <div>
                <input id="to_do" value="type task to add or task# for removal"/>
                <button type="button" onclick="todo('add')">
                    add task
                </button>
                <button type="button" onclick="todo('remove')">
                    remove task by #
                </button>
                <button type="button" onclick="main()">
                    back
                </button>
            </div>
            <p id="to_do_list_text"/>
        </div>
        <div id="notebook">
            <div>
                <input id="note_input" value="type note to add or # for removal"/>
                <button type="button" onclick="notes('add')">
                    add note
                </button>
                <button type="button" onclick="notes('remove')">
                    remove note by #
                </button>
                <button type="button" onclick="main()">
                    back
                </button>
            </div>
            <p id="note_text"/>
        </div>
        <div id="assignment">
            <div>
                <input id="assignment_input" value="type assignment to add or # for removal"/>
                <button type="button" onclick="Assignment('add')">
                    add assignment
                </button>
                <button type="button" onclick="Assignment('remove')">
                    remove assignment by #
                </button>
                <button type="button" onclick="main()">
                    back
                </button>
            </div>
            <p id="assignment_text"/>
        </div>
    </body>
    <script>
        let second="",minute="",hour="",day="",month="",year="",time="",now="";
        let text="",input="";
        let login_list=[];
        let forum_text="";
        let tdl_db=[],to_do_list=[],to_do_list_input="";
        let note_db=[],note=[],note_input="";
        let assignment_db=[],assignment=[],assignment_input="";
        function getTime()
        {
            now = new Date();
            second=now. getSeconds();
            minute=now. getMinutes();
            hour=now. getHours();
            day=now. getDate();
            month=now.getMonth() +1;
            year=now. getFullYear();
            time=year+"-"+month+"-"+day+" "+hour+":"+minute+":"+second;
        }
        function print(list,id,mode)
        {
            if(mode=="order")
                {text="<ol>";}
            if(mode=="unorder")
                {text="<ul>";}
            for(let i=0;i<(list.length);i++)
            {
                text+="<li>"+list[i]+"</li>";
            }
            if(mode=="order")
                {text+="</ol>";}
            if(mode=="unorder")
                {text+="</ul>";}
            document. getElementById(id).innerHTML=text;
        }
        function list_modify(list,input_id,action)
        {
            input=document.getElementById(input_id).value;
            if(action=="add")
            {
                list.push(input);
            }
            if(action=="remove")
            {
                list.splice(parseInt(input)-1,1);
            }
            return list;
        }
        function user_post()
        {
            document.getElementById("menu"). style. display="none";
            document.getElementById("login_post"). style. display="block";
            let userpost="", username="", user_class="", user_cn=0, identifier="", iden_no="";
        }
        function login_post(post)
        {
            userpost=post;
            document.getElementById("login_post"). style. display="none";
            document.getElementById("login"). style. display="block";
            if(post=="student")
            {
                document.getElementById("form"). innerHTML='<p>Name</p><input id="name" value=""/><p>Class</p><input id="class" value=""/><p>Class_number</p><input id="cn" value=""/><p>Password</p><input value=""/><button type="button" onclick="login()">login</button>';
            }
            if(post=="teacher")
            {
                document.getElementById("form"). innerHTML='<p>Name</p><input id="name" value=""/><p>Password</p><input value=""/><button type="button" onclick="login()">login</button>';
            }
            if(post=="class teacher")
            {
                document.getElementById("form"). innerHTML='<p>Name</p><input id="name" value=""/><p>Class</p><input id="class" value=""/><p>Password</p><input value=""/><button type="button" onclick="login()">login</button>';
            }
            if(post=="owner")
            {
                document.getElementById("form"). innerHTML='<p>Name</p><input id="name" value=""/><p>Password</p><input value=""/><button type="button" onclick="login()">login</button>';
            }
        }
        function login()
        {
            username=document. getElementById("name"). value;
            if(userpost!="teacher" && userpost!="owner")
            {
                user_class=document. getElementById("class"). value;
                if(userpost!="class teacher")
                {
                user_cn=document. getElementById("cn"). value;
                identifier=user_class+","+userpost;
                }
                else
                {
                    identifier=user_class+","+user_cn+","+userpost;
                }
            }
            else
            {
                identifier=username+","+userpost;
            }
            document. getElementById("greeting"). innerHTML="hi "+username+" !";
            if(!(login_list.includes(identifier)))
            {
                login_list.push(identifier);
            }
            iden_no=login_list.indexOf(identifier);
            main();
        }
        function main()
        {
            document. getElementById("login"). style. display="none";
            document. getElementById("head"). style. display="block";
            document. getElementById("main"). style. display="block";
            document. getElementById("forum"). style. display="none";
            document. getElementById("to_do_list"). style. display="none";
            document. getElementById("notebook"). style. display="none";
        }
        function redirect(site)
        {
            document. getElementById("main"). style. display="none";
            document. getElementById("head"). style. display="none";
            document. getElementById(site). style. display="block";
            if(tdl_db[iden_no]==undefined)
            {
                tdl_db[iden_no]=[];
            }
            to_do_list=tdl_db[iden_no];
            print(to_do_list,"to_do_list_text","order");
            if(note_db[iden_no]==undefined)
            {
                note_db[iden_no]=[];
            }
            note=note_db[iden_no];
            print(note,"note_text","order");
        }
        function forum_post()
        {
            forum_text+=document.getElementById("forum_input").value;
            forum_text+="<br>";
            getTime();
            forum_text+=time+" by "+username+"<br>";
            document. getElementById("forum_text"). innerHTML=forum_text;
        }
        function todo(action)
        {
            to_do_list=list_modify(to_do_list,"to_do",action)
            tdl_db[iden_no]=to_do_list;
            print(to_do_list,"to_do_list_text","order");
        }
        function notes(action)
        {
            note=list_modify(note,"note_input",action);
            note_db[iden_no]=note;
            print(note,"note_text","order");
        }
        function Assignment(action)
        {
            assignment=list_modify(assignment,"assignment_input",action);
            assignment_db[iden_no]=assignment;
            print(assignment,"assignment_text","order");
        }
        function sign_out()
        {
            if(confirm("Sign out?"))
            {
                document. getElementById("main"). style. display="none";
                document. getElementById("menu"). style. display="block";
            }
        }
    </script>
</html>
