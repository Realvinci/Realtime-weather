<template>
    <div>
        <p>{{ weather }}</p>     
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni, nihil? Reiciendis natus beatae quia saepe aspernatur eveniet amet dolore quas!</p>             
    </div>
  </template>
  
  <script>
import {app as app} from '../../firebase'
import { getStorage, ref, uploadBytesResumable, getDownloadURL } from "firebase/storage";
import { arrayUnion, getFirestore ,updateDoc} from "firebase/firestore";
import { doc, setDoc,addDoc,collection } from "firebase/firestore"; 
const storage = getStorage(app);
const db = getFirestore(app);

  export default {
   name:'weather',
   data(){
      return{
        weather:''
      }
   },
   methods:{
      async getWeather(c){
      try {
        console.log('this is the data')
        c.Header("Access-Control-Allow-Origin",`https://thingspeak.com/channels/2336821/feed.json`)
        c.Header("Access-Control-Allow-Methods", "GET, OPTIONS, POST, PUT")
        //const response = await fetch(`https://thingspeak.com/channels/2336821/feed.json`)
         console.log('this is the response from thinkspeak',response)
      } catch (error) {
        
      }
    },
     onGet() {
    const url = "https://thingspeak.com/channels/2336821/feeds.json";
    var headers ={}
    // var headers = {
    //     "Access-Control-Allow-Origin":"http://thinkspeak.com/channels/2336821/feed.json"
    
    // }
    
    fetch(url, {
        method : "GET",
        mode: 'cors',
        headers: headers
    })
    .then((response) => {
        if (!response.ok) {
            throw new Error(response.error)
        }
        console.log(response)
        return response.json();
    })
    
},
async test(){
    const docRef = await addDoc(collection(db, "WeatherData"), {
        weatherData:[{
      "channel": {
          "id": 2336821,
          "name": "Weather station",
          "latitude": "0.0",
          "longitude": "0.0",
          "field1": "Temperature (°C)",
          "field2": "Humidity (%)",
          "field3": "Pressure (mb)",
          "field4": "Light Intensity (Ω)",
          "field5": "Rainfall",
          "created_at": "2023-11-08T01:44:52Z",
          "updated_at": "2023-11-10T06:17:02Z",
          "last_entry_id": 131
      },
      "feeds": [
          {
              "created_at": "2023-11-08T06:42:43Z",
              "entry_id": 32,
              "field1": "26.20",
              "field2": "77.00",
              "field3": "911.36",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:43:04Z",
              "entry_id": 33,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.38",
              "field4": "831",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:43:24Z",
              "entry_id": 34,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.44",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:43:45Z",
              "entry_id": 35,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.34",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:44:05Z",
              "entry_id": 36,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.20",
              "field4": "0",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:44:26Z",
              "entry_id": 37,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.23",
              "field4": "634",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:44:46Z",
              "entry_id": 38,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.22",
              "field4": "639",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:45:06Z",
              "entry_id": 39,
              "field1": "26.70",
              "field2": "77.00",
              "field3": "911.12",
              "field4": "0",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:51:28Z",
              "entry_id": 40,
              "field1": "27.10",
              "field2": "77.00",
              "field3": "0.00",
              "field4": "113",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:51:48Z",
              "entry_id": 41,
              "field1": "27.10",
              "field2": "77.00",
              "field3": "nan",
              "field4": "119",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:52:09Z",
              "entry_id": 42,
              "field1": "27.10",
              "field2": "82.00",
              "field3": "nan",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T06:53:06Z",
              "entry_id": 43,
              "field1": "27.10",
              "field2": "84.00",
              "field3": "909.23",
              "field4": "100",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:53:26Z",
              "entry_id": 44,
              "field1": "27.10",
              "field2": "80.00",
              "field3": "909.19",
              "field4": "98",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T06:53:47Z",
              "entry_id": 45,
              "field1": "27.10",
              "field2": "80.00",
              "field3": "909.10",
              "field4": "99",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:46:04Z",
              "entry_id": 46,
              "field1": "26.30",
              "field2": "39.00",
              "field3": "0.00",
              "field4": "119",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T07:46:23Z",
              "entry_id": 47,
              "field1": "26.20",
              "field2": "39.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T07:46:40Z",
              "entry_id": 48,
              "field1": "26.20",
              "field2": "39.00",
              "field3": "0.00",
              "field4": "97",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:47:04Z",
              "entry_id": 49,
              "field1": "26.20",
              "field2": "39.00",
              "field3": "0.00",
              "field4": "121",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:47:25Z",
              "entry_id": 50,
              "field1": "25.80",
              "field2": "39.00",
              "field3": "0.00",
              "field4": "83",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:47:51Z",
              "entry_id": 51,
              "field1": "25.80",
              "field2": "39.00",
              "field3": "916.41",
              "field4": "115",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:48:12Z",
              "entry_id": 52,
              "field1": "25.30",
              "field2": "39.00",
              "field3": "915.89",
              "field4": "126",
              "field5": "0"
          },
          {
              "created_at": "2023-11-08T07:48:32Z",
              "entry_id": 53,
              "field1": "25.30",
              "field2": "39.00",
              "field3": "916.86",
              "field4": "80",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:39:53Z",
              "entry_id": 54,
              "field1": "28.10",
              "field2": "33.00",
              "field3": "0.00",
              "field4": "67",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:40:13Z",
              "entry_id": 55,
              "field1": "28.50",
              "field2": "32.00",
              "field3": "0.00",
              "field4": "82",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:43:12Z",
              "entry_id": 56,
              "field1": "28.50",
              "field2": "33.00",
              "field3": "0.00",
              "field4": "64",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:43:32Z",
              "entry_id": 57,
              "field1": "28.50",
              "field2": "33.00",
              "field3": "nan",
              "field4": "83",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:43:52Z",
              "entry_id": 58,
              "field1": "28.50",
              "field2": "32.00",
              "field3": "nan",
              "field4": "75",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T08:58:39Z",
              "entry_id": 59,
              "field1": "28.50",
              "field2": "32.00",
              "field3": "0.00",
              "field4": "69",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T09:19:00Z",
              "entry_id": 60,
              "field1": "26.70",
              "field2": "35.00",
              "field3": "0.00",
              "field4": "103",
              "field5": "1"
          },
          {
              "created_at": "2023-11-08T09:19:15Z",
              "entry_id": 61,
              "field1": "26.70",
              "field2": "35.00",
              "field3": "0.00",
              "field4": "131",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:23:03Z",
              "entry_id": 62,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:23:24Z",
              "entry_id": 63,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:23:44Z",
              "entry_id": 64,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:24:01Z",
              "entry_id": 65,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "1056",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:24:18Z",
              "entry_id": 66,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "1033",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:24:40Z",
              "entry_id": 67,
              "field1": "24.50",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "848",
              "field5": "0"
          },
          {
              "created_at": "2023-11-10T06:24:57Z",
              "entry_id": 68,
              "field1": "24.80",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "841",
              "field5": "0"
          },
          {
              "created_at": "2023-11-10T06:25:14Z",
              "entry_id": 69,
              "field1": "24.80",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:25:31Z",
              "entry_id": 70,
              "field1": "24.80",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:25:49Z",
              "entry_id": 71,
              "field1": "24.80",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T06:26:06Z",
              "entry_id": 72,
              "field1": "24.80",
              "field2": "73.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T21:40:06Z",
              "entry_id": 73,
              "field1": "27.10",
              "field2": "69.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T21:40:24Z",
              "entry_id": 74,
              "field1": "27.10",
              "field2": "68.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-10T21:41:46Z",
              "entry_id": 75,
              "field1": "27.60",
              "field2": "71.00",
              "field3": "0.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:13:21Z",
              "entry_id": 76,
              "field1": "33.80",
              "field2": "35.00",
              "field3": "892.78",
              "field4": "463",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:13:42Z",
              "entry_id": 77,
              "field1": "33.80",
              "field2": "34.00",
              "field3": "892.81",
              "field4": "90",
              "field5": "0"
          },
          {
              "created_at": "2023-11-11T15:14:02Z",
              "entry_id": 78,
              "field1": "33.80",
              "field2": "34.00",
              "field3": "892.68",
              "field4": "0",
              "field5": "0"
          },
          {
              "created_at": "2023-11-11T15:14:23Z",
              "entry_id": 79,
              "field1": "33.80",
              "field2": "35.00",
              "field3": "892.74",
              "field4": "112",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:14:44Z",
              "entry_id": 80,
              "field1": "33.80",
              "field2": "34.00",
              "field3": "892.71",
              "field4": "144",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:15:04Z",
              "entry_id": 81,
              "field1": "33.80",
              "field2": "33.00",
              "field3": "892.81",
              "field4": "121",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:15:25Z",
              "entry_id": 82,
              "field1": "33.80",
              "field2": "32.00",
              "field3": "892.80",
              "field4": "86",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:15:42Z",
              "entry_id": 83,
              "field1": "33.80",
              "field2": "32.00",
              "field3": "893.03",
              "field4": "45",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:26:38Z",
              "entry_id": 84,
              "field1": "33.80",
              "field2": "33.00",
              "field3": "892.99",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:26:58Z",
              "entry_id": 85,
              "field1": "33.80",
              "field2": "34.00",
              "field3": "892.89",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:53:32Z",
              "entry_id": 86,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.16",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:53:52Z",
              "entry_id": 87,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "893.94",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:54:14Z",
              "entry_id": 88,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.00",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:54:34Z",
              "entry_id": 89,
              "field1": "33.30",
              "field2": "29.00",
              "field3": "894.17",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:54:50Z",
              "entry_id": 90,
              "field1": "33.30",
              "field2": "29.00",
              "field3": "894.11",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:55:11Z",
              "entry_id": 91,
              "field1": "33.30",
              "field2": "27.00",
              "field3": "894.02",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:55:26Z",
              "entry_id": 92,
              "field1": "33.30",
              "field2": "27.00",
              "field3": "894.08",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:55:41Z",
              "entry_id": 93,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.15",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:56:02Z",
              "entry_id": 94,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.27",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:56:22Z",
              "entry_id": 95,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.29",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:56:42Z",
              "entry_id": 96,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.30",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:57:03Z",
              "entry_id": 97,
              "field1": "33.30",
              "field2": "29.00",
              "field3": "894.41",
              "field4": "142",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:57:23Z",
              "entry_id": 98,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.41",
              "field4": "160",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T15:57:44Z",
              "entry_id": 99,
              "field1": "33.30",
              "field2": "28.00",
              "field3": "894.32",
              "field4": "142",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:36:06Z",
              "entry_id": 100,
              "field1": "33.30",
              "field2": "34.00",
              "field3": "893.75",
              "field4": "51",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:36:27Z",
              "entry_id": 101,
              "field1": "33.30",
              "field2": "34.00",
              "field3": "893.86",
              "field4": "19",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:36:42Z",
              "entry_id": 102,
              "field1": "33.30",
              "field2": "32.00",
              "field3": "894.32",
              "field4": "51",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:37:03Z",
              "entry_id": 103,
              "field1": "33.30",
              "field2": "32.00",
              "field3": "894.14",
              "field4": "0",
              "field5": "0"
          },
          {
              "created_at": "2023-11-11T16:37:23Z",
              "entry_id": 104,
              "field1": "33.30",
              "field2": "33.00",
              "field3": "894.22",
              "field4": "0",
              "field5": "0"
          },
          {
              "created_at": "2023-11-11T16:37:44Z",
              "entry_id": 105,
              "field1": "33.30",
              "field2": "33.00",
              "field3": "894.56",
              "field4": "64",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:38:04Z",
              "entry_id": 106,
              "field1": "33.30",
              "field2": "32.00",
              "field3": "894.60",
              "field4": "48",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:38:25Z",
              "entry_id": 107,
              "field1": "33.30",
              "field2": "33.00",
              "field3": "894.49",
              "field4": "49",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:38:46Z",
              "entry_id": 108,
              "field1": "33.30",
              "field2": "32.00",
              "field3": "894.98",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:39:06Z",
              "entry_id": 109,
              "field1": "32.80",
              "field2": "33.00",
              "field3": "896.68",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:39:27Z",
              "entry_id": 110,
              "field1": "32.80",
              "field2": "32.00",
              "field3": "897.72",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T16:39:47Z",
              "entry_id": 111,
              "field1": "32.80",
              "field2": "33.00",
              "field3": "896.71",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-11T21:55:42Z",
              "entry_id": 112,
              "field1": "31.30",
              "field2": "68.00",
              "field3": "900.86",
              "field4": "0",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:22:18Z",
              "entry_id": 113,
              "field1": "24.80",
              "field2": "52.00",
              "field3": "915.07",
              "field4": "218",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:22:36Z",
              "entry_id": 114,
              "field1": "24.80",
              "field2": "53.00",
              "field3": "914.66",
              "field4": "1631",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:22:56Z",
              "entry_id": 115,
              "field1": "25.30",
              "field2": "50.00",
              "field3": "913.68",
              "field4": "355",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:23:21Z",
              "entry_id": 116,
              "field1": "25.80",
              "field2": "56.00",
              "field3": "912.62",
              "field4": "358",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:23:42Z",
              "entry_id": 117,
              "field1": "25.80",
              "field2": "56.00",
              "field3": "912.56",
              "field4": "458",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:24:00Z",
              "entry_id": 118,
              "field1": "25.80",
              "field2": "53.00",
              "field3": "912.42",
              "field4": "351",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:24:24Z",
              "entry_id": 119,
              "field1": "26.20",
              "field2": "55.00",
              "field3": "911.98",
              "field4": "306",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:26:00Z",
              "entry_id": 120,
              "field1": "27.10",
              "field2": "46.00",
              "field3": "909.18",
              "field4": "1584",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:26:18Z",
              "entry_id": 121,
              "field1": "27.60",
              "field2": "44.00",
              "field3": "908.59",
              "field4": "1602",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:26:43Z",
              "entry_id": 122,
              "field1": "27.60",
              "field2": "44.00",
              "field3": "907.66",
              "field4": "1771",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:27:41Z",
              "entry_id": 123,
              "field1": "28.50",
              "field2": "41.00",
              "field3": "905.33",
              "field4": "1739",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:28:02Z",
              "entry_id": 124,
              "field1": "28.90",
              "field2": "41.00",
              "field3": "904.54",
              "field4": "1789",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:28:22Z",
              "entry_id": 125,
              "field1": "29.30",
              "field2": "40.00",
              "field3": "903.92",
              "field4": "1767",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:29:31Z",
              "entry_id": 126,
              "field1": "30.20",
              "field2": "37.00",
              "field3": "901.40",
              "field4": "1786",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:29:51Z",
              "entry_id": 127,
              "field1": "30.80",
              "field2": "37.00",
              "field3": "900.90",
              "field4": "1661",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:41:15Z",
              "entry_id": 128,
              "field1": "33.30",
              "field2": "26.00",
              "field3": "896.86",
              "field4": "1841",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:41:47Z",
              "entry_id": 129,
              "field1": "33.80",
              "field2": "25.00",
              "field3": "896.24",
              "field4": "1786",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:43:01Z",
              "entry_id": 130,
              "field1": "34.20",
              "field2": "24.00",
              "field3": "894.21",
              "field4": "1812",
              "field5": "1"
          },
          {
              "created_at": "2023-11-14T08:43:19Z",
              "entry_id": 131,
              "field1": "34.30",
              "field2": "23.00",
              "field3": "893.56",
              "field4": "1786",
              "field5": "1"
          }
      ]
  }],
});


     }

   },
   
   created(){
   // this.Trainer();
     // this.getChild();
     //this.getRef()
     //this.getWeather()
     this.onGet()
     this.test()
   }
  }
  </script>
  
  <style>
  
  </style>