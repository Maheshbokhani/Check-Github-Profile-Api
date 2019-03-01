# Check Your Github Profile-(FetchApi)


![](https://cdn-images-1.medium.com/max/1600/1*safAvjgR68qpQCreDTOcYA.png)
   ![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQeo34UzEg1VMXlvv_biJ6hoROD6dt_kcW7zimjLD_vWxm2f7AUwQ) 


# Steps:
 
      $ react-native init projectname

* Make changes in App.js


       
        import React, { Component } from 'react';
        import { TouchableOpacity, View, Text, Image,TextInput} from 'react-native';
        import { ScrollView } from 'react-native-gesture-handler';



        export default class App extends Component {
          constructor(){
            super()
              this.state={
                url:'',
                username:'',
                name:'',
                email:'',
                location:'',
                 repo:''
              }
            this.handlePress.bind(this)
          }


          handlePress = async () => {

            fetch('https://api.github.com/users/'+this.state.username)

              .then(response => response.json())
              .then((responseJson)=>{

                this.setState({url:responseJson.avatar_url})
                this.setState({name:responseJson.name})
                this.setState({location:responseJson.location})
                this.setState({repo:responseJson.public_repos})
                this.setState({email:responseJson.email})


              })  
              .catch((error) => {
                  console.error(error);
              });
          }

            render(){
            return(


             <View style={{flex:1,paddingTop: 10,paddingLeft:15, backgroundColor:'#F8FFD1', }}>


              <Text style={{alignItems:'center',fontSize:22,fontWeight:'bold',height:50,color:'blue'}}>
              Check Github Profile</Text>


            <View style={{alignItems:'center',flexDirection:'row' }}>

             <TextInput style={{paddingLeft:5,height:45,borderWidth:1,width:200,borderColor:'blue'}}
             onChangeText={username => this.setState({ username })}
             placeholder='Enter github username'
             value={this.state.username}
             ></TextInput>


            <TouchableOpacity style={{marginLeft:5,backgroundColor:'#16F3BF',
            alignItems:'center',width:120,height:45,}} onPress={this.handlePress}>
             <Text style={{ color: '#000',paddingTop:13,fontSize:15,}}> Check Now </Text>
             </TouchableOpacity>

            </View>

          <View style={{alignItems:'flex-start',marginLeft:10,marginTop:20,flexDirection:'row' }}>
          <Text style={{fontSize:15,color:'black',width:50,height:40}}>
            Name:
            </Text>  
            <Text style={{fontSize:15,color:'black',width:70,height:40,marginLeft:3,width:150,color:'green'}}>
              {this.state.name}
            </Text>
          </View> 

          <View style={{alignItems:'flex-start',marginLeft:10,marginTop:10,flexDirection:'row' }}>
          <Text style={{fontSize:15,color:'black',width:50,height:40}}>
            Email:
            </Text>  
            <Text style={{fontSize:15,color:'black',width:70,height:40,marginLeft:3,width:150,color:'green'}}>
              {this.state.email}
            </Text>
          </View> 

        <View style={{alignItems:'flex-start',marginLeft:10,marginTop:10,flexDirection:'row' }}>
        <Text style={{fontSize:15,color:'black',width:65,height:40}}>
          Location:
          </Text>  
          <Text style={{fontSize:15,color:'black',width:70,height:40,marginLeft:3,width:150,color:'green'}}>
            {this.state.location}
          </Text>
        </View>

        <View style={{alignItems:'flex-start',marginLeft:10,marginTop:10,flexDirection:'row' }}>
        <Text style={{fontSize:15,color:'black',width:90,height:40}}>
          Repositories:
          </Text>  
          <Text style={{fontSize:15,color:'black',width:70,height:40,marginLeft:3,width:150,color:'green'}}>
            {this.state.repo}
          </Text>
        </View> 


       <View style={{flexDirection:'row',marginTop:10}}>
        <Text style={{fontSize:15,color:'black',width:100,height:40,marginLeft:10,}}>
          Profile Picture:
          </Text>  

        <Image
                style={{width: 170, height: 170,marginLeft:5}}
                source={{uri: this.state.url}}
              />
        </View>

         </View> 

        );
      }
      }
      

* First of start server

      $ react-native start 
    OR
      
      $ npm start
   

* Run Application in android

      $ react-native run-android
      
      

* Run Application in IOS

      $ react-native run-ios


# Notes:

* If find error for react-native-gesture-handler, so install this in the terminal

         $ npm install --save react-native-gesture-handler
         $ react-native link react-native-gesture-handler
         
 

