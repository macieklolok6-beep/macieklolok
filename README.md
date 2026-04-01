const handleMapPress = (e) => {
  const { latitude, longitude } = e.nativeEvent.coordinate;
  
  // Tutaj w przyszłości otworzymy formularz
  alert(`Chcesz dodać spot na współrzędnych: ${latitude}, ${longitude}?`);
};

// W widoku mapy dodajemy:
<MapView onPress={handleMapPress}> ... </MapView>
