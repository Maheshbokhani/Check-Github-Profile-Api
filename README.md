# Check Your Github Profile-Api


![](https://cdn-images-1.medium.com/max/1600/1*safAvjgR68qpQCreDTOcYA.png)
   ![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQeo34UzEg1VMXlvv_biJ6hoROD6dt_kcW7zimjLD_vWxm2f7AUwQ) 


# Steps:
 
      $ react-native init projectname

* Make changes in App.js


       
          
         import React, { Component } from 'react';
         import { TouchableOpacity, View, Text, Image, TextInput,StyleSheet } from 'react-native';
         import { ScrollView } from 'react-native-gesture-handler';



         export default class App extends Component {
           constructor() {
             super()
             this.state = {
               url: '',
               username: '',
               name: '',
               email: '',
               location: '',
               repo: ''
             }
             this.handlePress.bind(this)
           }


           handlePress = async () => {

             fetch('https://api.github.com/users/' + this.state.username)

               .then(response => response.json())
               .then((responseJson) => {

                 this.setState({ url: responseJson.avatar_url ,name: responseJson.name,
                 location: responseJson.location,
                   repo: responseJson.public_repos, email: responseJson.email 
                 })
               })
               .catch((error) => {
                 console.error(error);
               });
           }

           render() {
             return (

          <ScrollView  style={styles.container}>

         <View>


          <Text style={styles.titleText}>Check Github Profile</Text>


          <View style={{ alignItems: 'center', flexDirection: 'row' }}>

            <TextInput style={styles.textInput}
              onChangeText={(username) => this.setState({ username })}
              placeholder='Enter github username'
              value={this.state.username}
            ></TextInput>


            <TouchableOpacity style={styles.button} onPress={this.handlePress}>
              <Text style={styles.buttonText}> Check Now </Text>
            </TouchableOpacity>

          </View>

          <View style={styles.Views}>
            <Text style={styles.text}>
              Name:
            </Text>
            <Text style={styles.fetchText}>
              {this.state.name}
            </Text>
          </View>

          <View style={styles.Views}>
            <Text style={styles.text}>
              Email:
           </Text>
            <Text style={styles.fetchText}>
              {this.state.email}
            </Text>
          </View>

          <View style={styles.Views}>
            <Text style={styles.text}>
              Location:
          </Text>
            <Text style={styles.fetchText}>
              {this.state.location}
            </Text>
          </View>

          <View style={styles.Views}>
            <Text style={styles.text}>
              Repositories:
            </Text>
            <Text style={styles.fetchText}>
              {this.state.repo}
            </Text>
          </View>


             <View style={styles.Views}>
               <Text style={styles.text}>
                 Profile Picture:
               </Text>

               <Image
                 style={styles.imageset}
                 source={{ uri: this.state.url }}
               />
             </View>

           </View>

         </ScrollView>

          );
        }
      }

         const styles=StyleSheet.create({

           container:{
             flex: 1, paddingTop: 10, paddingLeft: 15, backgroundColor: '#F8FFD1'
           },

           titleText:{
             alignItems: 'center', fontSize: 22, fontWeight: 'bold', height: 50, color: 'blue'
           },

           textInput:{
              paddingLeft: 5, height: 45, borderWidth: 1, width: 200, borderColor: 'blue' 
             },

           button:{
              marginLeft: 5, backgroundColor: '#16F3BF', alignItems: 'center', width: 120, height: 45, 
           },

           Views:{ alignItems: 'flex-start', marginLeft: 10, marginTop: 20, flexDirection: 'row' },

          text:{ fontSize: 15, color: 'black', width: 130, height: 40 },

          imageset:{ width: 170, height: 170, marginLeft: 5 },

          fetchText:{ 
            fontSize: 15, color: 'black', width: 70, 
            height: 40, marginLeft: 3, width: 150, color: 'green' 
           },

          buttonText:{ color: '#000', paddingTop: 13, fontSize: 15, }

         })
      

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
         
 
# Output:

![](https://firebasestorage.googleapis.com/v0/b/imagestore-b2432.appspot.com/o/Screenshot_2019-03-01-12-50-18%20(1).png?alt=media&token=7fca39f2-2314-449e-b933-f04ff5d8d304) ![](https://firebasestorage.googleapis.com/v0/b/imagestore-b2432.appspot.com/o/Screenshot_2019-03-01-12-50-35.png?alt=media&token=e4d10a47-6404-49d1-b2b0-dbafe9825dc5)


