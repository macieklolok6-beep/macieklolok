const handleMapPress = (e) => {
  const { latitude, longitude } = e.nativeEvent.coordinate;
  
  // Tutaj w przyszłości otworzymy formularz
  alert(`Chcesz dodać spot na współrzędnych: ${latitude}, ${longitude}?`);
};

// W widoku mapy dodajemy:
<MapView onPress={handleMapPress}> ... </MapView>

import { getDatabase, ref, push } from "firebase/database";

const saveSpot = (name, type, lat, lng) => {
  const db = getDatabase();
  const spotsRef = ref(db, 'spots'); // Tworzymy "szufladę" o nazwie 'spots'

  push(spotsRef, {
    name: name,
    type: type,
    location: {
      latitude: lat,
      longitude: lng
    },
    createdAt: Date.now() // Zapisujemy, kiedy spot został dodany
  })
  .then(() => alert("Spot dodany! Piona!"))
  .catch((error) => console.error("Coś poszło nie tak:", error));
};
