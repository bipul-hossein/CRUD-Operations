#### Go To- src > Pages > Home > Home.js

// Get
useEffect(() => {
        fetch('http://localhost:5000/users')
            .then(res => res.json())
            .then(data => setUsers(data))
}, [])


// POST example
// step_1. create a post Api in Server site
// step_2. uploading json data with method,headers,body; like this-
/* ----------See the exam. in mozilla doc-------------- */
fetch('http://localhost:5000/users', {
method: 'POST',
 headers: {
'Content-Type': 'application/json',
},
body: JSON.stringify(user),
})
            .then(response => response.json())
  .then(data => {
    console.log('Success:', data);
    const newUsers = [...users, data];
    setUsers(newUsers)
  })
  .catch(error => {
    console.error('Error:', error);
  });
  
  //server site
  // step_4 receive req with(req.body);
  // step_5 stop undefine data use middle ware (app.use(express.json());)    
  event.target.reset()
    }

// DELETE
  const handleDelete = user => {
  const agree = window.confirm(`you want to delete${user.name}`)
  if (agree) {
  // console.log(`you want to delete${user._id}`)
  fetch(`http://localhost:5000/users/${user._id}`, {
  method: 'DELETE',
  })
   
.then(response => response.json())
  .then(data => {
    console.log('Success:', data);
    if (data.deletedCount > 0) {
      alert('User delete successfully')
      const remainingUsers = users.filter(usr => usr._id !== user._id)
      setUsers(remainingUsers)
    }
  })
  .catch(error => {
    console.error('Error:', error);
  });             
  }
  }
