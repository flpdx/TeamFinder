# TeamFinder

### TeamFinder é uma aplicação móvel desenvolvida com o React Native com o intuito de permitir aos usuários conexões entre contas cadastradas, interação e incentivo a prática de atividades físicas. A ideia é conseguir aproximar jovens e adultos de uma vida mais saudável e ativa.

## Metas

### O TeamFinder tem o objetivo de possuir uma plataforma de navegação simples e acessível. A ideia é que o aplticativo consiga registrar o usuário, direciona-lo para um chat específico da modalidade, enviar e receber mensagens.

### Capturas de tela

![](https://github.com/flpdx/TeamFinder/blob/main/WhatsApp%20Image%202023-04-18%20at%2020.43.08.jpeg)
![](https://github.com/flpdx/TeamFinder/blob/main/WhatsApp%20Image%202023-04-18%20at%2020.43.45.jpeg)
![](https://github.com/flpdx/TeamFinder/blob/main/WhatsApp%20Image%202023-04-18%20at%2020.45.01.jpeg)



#### Código

```javascript
import React, { useState } from 'react';
import { StyleSheet, Text, View, TextInput, Button, FlatList, TouchableOpacity, ScrollView, SafeAreaView,  } from 'react-native';
import { MaterialCommunityIcons } from '@expo/vector-icons';
import { Entypo } from '@expo/vector-icons';
import { MaterialIcons } from '@expo/vector-icons';

const sports = [
  { id: '1', name: 'Futebol' },
  { id: '2', name: 'Basquete' },
  { id: '3', name: 'Tênis' },
  { id: '4', name: 'Natação' },
  { id: '5', name: 'Ciclismo' },
  { id: '6', name: 'Vôlei' },
  { id: '6', name: 'Skateboard' },
];

export default function Mid() {
  const [search, setSearch] = useState('');
  const [filteredSports, setFilteredSports] = useState(sports);

  const handleSearch = () => {
    const filtered = sports.filter((sport) => sport.name.toLowerCase().includes(search.toLowerCase()));
    setFilteredSports(filtered);
  };

  const renderSport = ({ item }) => (
    <TouchableOpacity style={styles.sport} onPress={() => alert(`Você selecionou ${item.name}`)}>
      <Text style={styles.sportText}>{item.name}</Text>
      <MaterialCommunityIcons name="chevron-right" size={24} color="black" />
    </TouchableOpacity>
  );

  return (
    <ScrollView>
        <View style={styles.container}>
            <Text style={styles.cover}>TeamFinder<MaterialIcons name="sports-football" size={40} color="black" /></Text>
            <Text style={styles.message}>Conecte-se através do esporte</Text>
            <Text style={styles.login}>Login</Text>
            <Text style={styles.password}>Senha</Text>
            <Text style={styles.register}>Cadastre-se</Text>
            <Text style={styles.title}>TeamFinder<MaterialIcons name="sports-football" size={40} color="#71F79F" /></Text>
             
          <View style={styles.search}>
              <TextInput style={styles.searchInput} onChangeText={setSearch} value={search} placeholder="Pesquisar modalidade..." />
              <Button title="Buscar" onPress={handleSearch} />
          </View>
            <ScrollView>
              <FlatList data={filteredSports} renderItem={renderSport} keyExtractor={(item) => item.id} />
            </ScrollView>
            <Text style={styles.cointer2}></Text>
            <Text style={styles.chat}>Chat Aberto <Entypo name="chat" size={24} color="black" alignItems="right" /></Text>
          <Text style={styles.chatbox}></Text>
            <Text style={styles.chatMessage}> Mensagem  <MaterialIcons name="send" size={20} color="black" /></Text>
        </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  
  container: {
    flex: 1,
    // alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#429EA6',
    padding: 10,
  },

  cover: {
    fontSize: 45,
    fontWeight: 'bold',
    color: 'black',
    padding: 10,
    marginTop: 180,
    marginBottom: 0,
    textAlign: 'left',
    display: 'flex',
    alignItems: 'Center',
  },
  message: {
    color:'black',
    fontSize:15,
    fontWeight: 'bold',
    padding: 1,
    marginTop: 0,
    marginBottom: 120,
    borderRadius: 5,
    textAlign: 'center',
  },
  login:{
    color:'black',
    fontSize:25,
    backgroundColor:"#fff",
    padding: 10,
    marginTop: 50,
    marginBottom: 5,
    borderRadius: 5,
    textAlign: 'center',
  },
  password:{
    color:'black',
    fontSize:25,
    backgroundColor:"#fff",
    padding: 10,
    marginTop: 0,
    marginBottom: 2,
    borderRadius: 5,
    textAlign: 'center',
  },
  register:{
    color:'black',
    fontSize:15,
    padding: 10,
    marginTop: 2,
    marginBottom: 70,
    borderRadius: 5,
    textAlign: 'center',
  },
  title: {
    fontSize: 40,
    fontWeight: 'bold',
    backgroundColor: '#153B50',
    color: '#71F79F',
    padding: 10,
    marginTop: 70,
    marginBottom: 20,
    borderRadius: 5,
    textAlign: 'center',
  },
  search: {
    flexDirection: 'row',
    alignItems: 'center',
    marginBottom: 20,
  },
  searchInput: {
    flex: 1,
    borderWidth: 1,
    borderColor: '#153B50',
    padding: 10,
    marginRight: 10,
    borderRadius: 5,
  },
  sport: {
    flexDirection: 'row',
    // alignItems: 'center',
    justifyContent: 'space-between',
    borderWidth: 1,
    borderColor: '#153B50',
    padding: 10,
    borderRadius: 5,
    marginBottom: 10,
  },
  sportText: {
    fontSize: 18,
    color: '#153B50',
  },
  chat: {
    fontSize: 20,
    fontWeight: 'bold',
    backgroundColor: '#153B50',
    color: 'black',
    padding: 10,
    marginTop: 120,
    marginBottom: 1,
    borderRadius: 5,
    textAlign: 'left',
    display: 'flex',
    justifyContent: 'space-between',
    alignItems: 'Center',
  },
   chatbox: {
    fontSize: 20,
    backgroundColor: '#fff',
    padding: 120,
    marginTop: 1,
    marginBottom: 0,
    borderRadius: 14,
    textAlign: 'left',
  },
  chatMessage: {
    fontSize: 15,
    fontWeight: 'bold',
    flexDirection: 'row',
    padding: 10,
    marginTop: 0,
    marginBottom: 1,
    borderRadius: 15,
    textAlign: 'left',
    justifyContent: 'space-between',
    borderWidth: 2,
    display: 'flex',
    borderColor: '#153B50',
  }
});
       
