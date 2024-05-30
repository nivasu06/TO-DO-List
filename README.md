<!DOCTYPE html>
<html>
<head>
    <title>To Do List</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
    body{
            background-image: url("https://images.inc.com/uploaded_files/image/1920x1080/getty_514914078_200013332000928076_167571.jpg");

        }
        .container{
            display:flex;
            justify-content: center;
            align-items: center;
            height:100vh;
        }
        .boxes{
            width: 80%;
            max-width: 600px;
            padding:20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            background-color: #30B7CD;
        }
        h1{
            text-align: center;
        }
        #header{
            margin-bottom: 20px;
        }
        #footer {
            margin-top: 20px;
            text-align: center;
        }
        #todo{
            width: 90%;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
            box-sizing: border-box;
            margin-bottom: 10px;
        }
        #todo-list {
            list-style-type: none;
            padding: 0;
        }
        li {
            margin-bottom: 10px;
            display:flex;
            align-items: center;
        }
        input[type="checkbox"] {
            margin-right: 10px;
            width:20px;
            height: 20px;
            border-radius: 50%;
        }
        .delete-btn{
            background: none;
            border: none;
            cursor: pointer;
        }
        .delete-btn i{
            color:red;
            font-size:1.2em;
            vertical-align: middle;
            margin-left: 5px;
        }
        label{
            flex-grow: ;
        }

</style>
</head>
<body>
    <div class="container">
        <div class="boxes">
                <h1>DO LIST</h1>
                <section id='header'>
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-card-checklist" viewBox="0 0 16 16">
              <path d="M14.5 3a.5.5 0 0 1 .5.5v9a.5.5 0 0 1-.5.5h-13a.5.5 0 0 1-.5-.5v-9a.5.5 0 0 1 .5-.5zm-13-1A1.5 1.5 0 0 0 0 3.5v9A1.5 1.5 0 0 0 1.5 14h13a1.5 1.5 0 0 0 1.5-1.5v-9A1.5 1.5 0 0 0 14.5 2z"/>
              <path d="M7 5.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5m-1.496-.854a.5.5 0 0 1 0 .708l-1.5 1.5a.5.5 0 0 1-.708 0l-.5-.5a.5.5 0 1 1 .708-.708l.146.147 1.146-1.147a.5.5 0 0 1 .708 0M7 9.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5m-1.496-.854a.5.5 0 0 1 0 .708l-1.5 1.5a.5.5 0 0 1-.708 0l-.5-.5a.5.5 0 0 1 .708-.708l.146.147 1.146-1.147a.5.5 0 0 1 .708 0"/>
            </svg>
                    <input type="text" id="todo"  placeholder ="add to do">

                    <button onclick="addTask()"class='btn-1'>
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-file-plus-fill" viewBox="0 0 16 16">
              <path d="M12 0H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h8a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2M8.5 6v1.5H10a.5.5 0 0 1 0 1H8.5V10a.5.5 0 0 1-1 0V8.5H6a.5.5 0 0 1 0-1h1.5V6a.5.5 0 0 1 1 0"/>
            </svg>
                    </button>
                </section>
                <section id='bodier'>
                            <ul id='todo-list'></ul>
                        </section>
                        <section id='footer'>
                            <div class="task-remain">
                                Remaining Task Left:<span id="remaining-task">0</span>
                                
                            </div>
                            <br>
                            <button onclick="CHECKALL()" class='btn-2'> CHECK ALL</button>
                            <button onclick="ALLREMOVE()" class='btn-2'>REMOVE ALL</button>
                        </section>
            </div>
    </div>
    <script type="text/javascript">
                function addTask(){
                    var item=document.getElementById('todo');
                    var Itext=item.value.trim();
                    if(Itext===''){
                        alert('please enter something');
                        return;
                    }
                    var li=document.createElement('li');
                    var checkbox=document.createElement('input');
                    checkbox.type='checkbox';
                    checkbox.onclick=function(){
                        var confirms=confirm('the task completed it is removed');
                        if(confirms){
                            li.remove();

                        }
                        
                        updateRemaining();

                    }
                    var label = document.createElement('label');
                    label.textContent = Itext;
                    var deltbtn=document.createElement("button");
                    deltbtn.className="delete-btn";
                    var icon=document.createElement('i');
                    icon.className="fas fa-trash-alt"; 
                    deltbtn.appendChild(icon);

                    deltbtn.onclick=function(){
                        li.remove();
                        updateRemaining();
                    }

                    li.appendChild(checkbox);
                    li.appendChild(label);
                    li.appendChild(deltbtn);
                    document.getElementById('todo-list').appendChild(li);
                    item.value = '';
                    updateRemaining();

                }
                function CHECKALL(){
                    var checkall=document.querySelectorAll('input[type="checkbox"]');
                    checkall.forEach(function(checkbox){
                        checkbox.checked=true;
                    });

                }
                function ALLREMOVE(){
                    var todolist=document.getElementById('todo-list');
                    var confirms=confirm('THE ALL TASKS ARE REMOVED');
                        if(confirms){
                            todolist.innerHTML='';

                        }
            
                    
                    updateRemaining();
                }

                function updateRemaining(){
                    var remaining=document.getElementById('todo-list').getElementsByTagName('li').length;
                    document.getElementById('remaining-task').textContent=remaining;
                }
     </script>
</body>
</html>

