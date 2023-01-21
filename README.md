# hooksUseEffect

import React , { useState } from 'react';
import './App.css';
import { useEffect } from 'react';

function App() {

  const[res,setRes] =useState('posts')
  const[items,setItems] = useState([])

  useEffect(()=>{
    fetch(`https://jsonplaceholder.typicode.com/${res}`)
      .then(response => response.json())
      .then(json => setItems(json))
  }, [res])

  return (
    <div className="App">
      <h3>{res}</h3>
	    <button onClick={()=>setRes('posts')}>Post</button>
      <button onClick={()=>setRes('comments')}>comment</button>
      <button onClick={()=>setRes('users')}>users</button>

{items.map(item =>{
  return <pre>{JSON.stringify(item)}</pre>
})}
    </div>
  );
}

export default App;
