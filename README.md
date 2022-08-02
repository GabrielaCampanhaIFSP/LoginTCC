# LoginTCC
import {
  StyleSheet,
  Text,
  View,
  TextInput,
  Image,
  Button,
  TouchableOpacity,
  ImageBackground
} from "react-native";
import styles from "./styles";
import React,{useState} from 'react'
import axios from 'axios';

export default function Login({ navigation }) {

  const [edv,setEDV] = useState('')
  const [password,setPassword] = useState('')

  

  const login=()=>{
    console.log(password);
    console.log(edv);
    axios.post('http://127.0.0.1:5000/auth',{
      username:Number(edv),
      password:password,
      
    }).then((e)=>{console.log(e)})
  }
  return (
    <View style={styles.container}>
      
      <View style={styles.header}>
        <Image
            style={{width: 140, height: 140, resizeMode: 'contain', marginLeft: 15}}
            source={require(".././../../assets/logo_bosch.png")}
        />
      </View>


      <View style={styles.content}>
                <Image
                    style={{height: 190, width: 190, resizeMode: 'contain',marginTop: 20}}
                    source={require(".././../../assets/map.png")}
                />
                <Text style={styles.title}>Welcome</Text>


                <View style={styles.form}>

                    <TextInput style={styles.input} placeholder="EDV" value={edv} onChange={(e)=>setEDV(e.target.value)} />
                    <TextInput style={styles.input} placeholder="Password" value={password} onChange={(e)=>setPassword(e.target.value)}/>

                    <TouchableOpacity
                    style={styles.buttonEnter}
                    // onPress={() => navigation.navigate("Home")}
                    onPress={login}
                    >
                      <Text style={styles.textButtonEnter}>Enter</Text>
                    </TouchableOpacity>

                    <TouchableOpacity
                    // onPress={() => navigation.navigate("Home")}
                    >
                      <Text style={styles.Link}>First Acess</Text>
                    </TouchableOpacity>

                </View>
      </View>
      

      <View style={styles.footer}>
        <ImageBackground source={require(".././../../assets/supergraphic.jpg")} resizeMode="cover" style={styles.supergraphic}/>
      </View>

    </View>
  );
}
