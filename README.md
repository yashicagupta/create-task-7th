//
//  ContentView.swift
//  Astrology-CreateTask7th
//
//  Created by Brinda Morisetty on 4/11/24.
//
import SwiftUI

// Defined the ZodiacSign struct to hold information about each zodiac sign
struct ZodiacSign {
    let name: String
    let startDate: DateComponents
    let endDate: DateComponents
    let element: String
    let qualities: String
    let compatibility: String
    
}

// Defined a list of zodiac signs with their respective date ranges, elements, qualities, and compatibility.
let zodiacSigns: [ZodiacSign] = [
    ZodiacSign(name: "Aquarius", startDate: DateComponents(month: 1, day: 20), endDate: DateComponents(month: 2, day: 18), element: "Air", qualities: "Innovative, Original.  Aquarius is innovative and independent, valuing individuality and humanitarian causes. Their intellectual and progressive nature leads to original ideas, but they may struggle with emotional detachment and stubbornness. Aquarians seek intellectual freedom and meaningful connections.", compatibility: "Love compatibility: Aries - 68, Taurus - 11, Gemini- 85, Cancer - 31, Leo - 89, Virgo - 30, Libra - 68, Scorpio - 30, Sagittarius - 83, Capricorn - 37, Aquarius - 75, Pisces - 38"),
    ZodiacSign(name: "Pisces", startDate: DateComponents(month: 2, day: 19), endDate: DateComponents(month: 3, day: 20), element: "Water", qualities: "Compassionate, Intuitive. Pisces is compassionate and imaginative, known for their empathetic and dreamy nature. Their creativity and intuition guide them, but they can be overly sensitive and prone to escapism. Pisces desires emotional connections and artistic expression, often drawn to spiritual pursuits.", compatibility: "Love compatibility: Aries - 29%, Taurus - 88%, Gemini - 10%, Cancer - 72%, Leo - 14%, Virgo - 86%, Libra - 29%, Scorpio - 81%, Sagittarius - 50%, Capricorn - 76%, Aquarius - 38%, Pisces - 73%"),
    ZodiacSign(name: "Aries", startDate: DateComponents(month: 3, day: 21), endDate: DateComponents(month: 4, day: 19), element: "Fire", qualities: "Confident, Courageous. Aries is an energetic and confident leader who thrives on challenges and adventure. Their boldness and courage can inspire others, but they can also be impulsive and impatient. While they bring passion to everything they do, they must learn to consider others' perspectives and take time to plan.", compatibility: "Aries -  75%, Taurus - 63%, Gemini- 74%, Cancer - 47%, Leo - 83%, Virgo - 42%, Libra - 62%, Scorpio - 48%, Sagittarius - 87%, Capricorn - 38%, Aquarius - 58%, Pisces - 29%"),
    ZodiacSign(name: "Taurus", startDate: DateComponents(month: 4, day: 20), endDate: DateComponents(month: 5, day: 20), element: "Earth", qualities: "Reliable, Patient.  Taurus is a grounded and dependable individual who values stability and comfort. Their persistence and loyalty make them excellent friends and partners, though they can be stubborn and resistant to change. Taurus finds joy in life's simple pleasures and seeks long-lasting, meaningful connections.", compatibility: "Aries -  63%, Taurus - 86%, Gemini- 23%, Cancer - 91%, Leo - 29%, Virgo - 73%, Libra - 33%, Scorpio - 81%, Sagittarius - 31%, Capricorn - 89%, Aquarius - 11%, Pisces - 88%"),
    ZodiacSign(name: "Gemini", startDate: DateComponents(month: 5, day: 21), endDate: DateComponents(month: 6, day: 20), element: "Air", qualities: "Adaptable, Outgoing. Gemini is a curious and sociable sign that loves to communicate and learn new things. Their adaptability and charm allow them to connect with diverse people, but they may struggle with indecisiveness and restlessness. Geminis thrive on intellectual stimulation and variety in their lives.", compatibility: "Aries -  68%, Taurus - 11%, Gemini- 85%, Cancer - 21%, Leo - 89%, Virgo - 30%, Libra - 68%, Scorpio - 30%, Sagittarius - 83%, Capricorn - 37%,Aquarius - 75%, Pisces - 38%"),
    ZodiacSign(name: "Cancer", startDate: DateComponents(month: 6, day: 21), endDate: DateComponents(month: 7, day: 22), element: "Water", qualities: "Nurturing, Intuitive. Cancer is a nurturing and empathetic sign known for their strong emotional bonds. Their intuition and loyalty make them protective of their loved ones, though they can be overly sensitive and prone to mood swings. Cancer seeks deep connections and values a supportive, loving environment.", compatibility: "Aries -  47%, Taurus - 91%, Gemini- 21%, Cancer - 85%, Leo - 29%, Virgo - 77%, Libra - 28%, Scorpio - 79%, Sagittarius - 27%, Capricorn - 84%, Aquarius - 31%, Pisces - 72%,"),
    ZodiacSign(name: "Leo", startDate: DateComponents(month: 7, day: 23), endDate: DateComponents(month: 8, day: 22), element: "Fire", qualities: "Charismatic, Creative.  Leo is a charismatic and confident leader who thrives on attention and admiration. Their passion and creativity bring life to any situation, but they can be prone to arrogance and a need for validation. Leos seek recognition and opportunities to shine, always eager to leave their mark.", compatibility: "Aries -  83%, Taurus - 29%, Gemini- 82%, Cancer - 29%, Leo - 78%, Virgo - 35%, Libra - 75%, Scorpio - 29%, Sagittarius - 75%, Capricorn - 27%, Aquarius - 89%, Pisces - 14%"),
    ZodiacSign(name: "Virgo", startDate: DateComponents(month: 8, day: 23), endDate: DateComponents(month: 9, day: 22), element: "Earth", qualities: "Detail-oriented, Analytical. Virgo is detail-oriented and practical, with a focus on precision and efficiency. Their analytical mind and dedication to improvement can lead to great accomplishments, though they may struggle with perfectionism and self-criticism. Virgos desire order and strive to be of service to others.", compatibility: "Aries -  42%, Taurus - 73%, Gemini- 40%, Cancer - 77%, Leo - 35%, Virgo - 65%, Libra - 30%, Scorpio - 76%, Sagittarius - 32%, Capricorn - 77%, Aquarius - 30%, Pisces - 86%"),
    ZodiacSign(name: "Libra", startDate: DateComponents(month: 9, day: 23), endDate: DateComponents(month: 10, day: 22), element: "Air", qualities: "Diplomatic, Balanced. Libra is charming and diplomatic, seeking harmony and balance in all aspects of life. Their fairness and empathy make them great mediators, but they can be indecisive and overly focused on pleasing others. Libras value aesthetics and long for harmonious relationships.", compatibility: "Aries -  62%, Taurus - 33%, Gemini- 78%, Cancer - 28%, Leo - 75%, Virgo - 30%, Libra - 68%, Scorpio - 29%, Sagittarius - 71%, Capricorn - 34%, Aquarius - 68%, Pisces - 29%"),
    ZodiacSign(name: "Scorpio", startDate: DateComponents(month: 10, day: 23), endDate: DateComponents(month: 11, day: 21), element: "Water", qualities: "Intense, Passionate. Scorpio is intense and passionate, known for their depth of emotion and determination. Their resourcefulness and loyalty make them strong allies, but they can be secretive and possessive. Scorpios seek truth and transformation, often delving into mysteries and the unknown.", compatibility: "Aries -  48%, Taurus - 89%, Gemini- 15%, Cancer - 79%, Leo - 29%, Virgo - 76%, Libra - 29%, Scorpio - 66%, Sagittarius - 30%, Capricorn - 64%, Aquarius - 30%, Pisces - 81%"),
    ZodiacSign(name: "Sagittarius", startDate: DateComponents(month: 11, day: 22), endDate: DateComponents(month: 12, day: 21), element: "Fire", qualities: "Adventurous, Optimistic. Sagittarius is adventurous and optimistic, always seeking new experiences and knowledge. Their enthusiasm and open-mindedness attract others, but they can be blunt and tactless. Sagittarians value freedom and strive to explore the world and expand their horizons.", compatibility: "Aries -  87%, Taurus - 31%, Gemini- 92%, Cancer - 27%, Leo - 75%, Virgo - 32%, Libra - 71%, Scorpio - 30%, Sagittarius - 74%, Capricorn - 38%, Aquarius - 83%, Pisces - 50%"),
    ZodiacSign(name: "Capricorn", startDate: DateComponents(month: 12, day: 22), endDate: DateComponents(month: 1, day: 19), element: "Earth", qualities: "Disciplined, Responsible.  Capricorn is ambitious and disciplined, with a focus on long-term goals and achievement. Their practicality and responsibility lead to success, though they can be overly cautious and serious. Capricorns desire recognition and stability, working hard to achieve their objectives.", compatibility: "Aries -  38%, Taurus - 89 %, Gemini- 15%, Cancer - 84%, Leo - 27%, Virgo - 77%, Libra - 34%, Scorpio - 64%, Sagittarius - 38%, Capricorn - 62%, Aquarius - 37%, Pisces - 76%"),
]

// Define a function to calculate the zodiac sign based on the user's birthday
func calculateZodiacSign(birthday: DateComponents) -> ZodiacSign? {
    for sign in zodiacSigns {
        let startDate = Calendar.current.date(from: sign.startDate)!
        let endDate = Calendar.current.date(from: sign.endDate)!
        let userDate = Calendar.current.date(from: birthday)!
        
        // Check if the user's birthday falls within the date range of the current zodiac sign
        if (userDate >= startDate && userDate <= endDate) ||
           (sign.startDate.month == 12 && userDate <= endDate) ||
           (sign.endDate.month == 12 && userDate >= startDate) {
            return sign
        }
    }
    return nil
}

// Define the main SwiftUI app
struct ContentView: View {
    @State private var birthday: Date = Date()
    @State private var zodiacSign: ZodiacSign?
    @State private var showZodiacInfo: Bool = false
    
    var body: some View {
        NavigationView {
            VStack {
                // Welcome page
                Text("Find Your Astrology Sign")
                    .font(.largeTitle)
                    .padding()
                
                // Input for birthday
                DatePicker("Enter your birthday:", selection: $birthday, displayedComponents: [.date])
                    .datePickerStyle(WheelDatePickerStyle())
                    .padding()
                
                // Button to find zodiac sign
                Button("Find My Zodiac Sign") {
                    // Calculate zodiac sign based on the entered birthday
                    let birthdayComponents = Calendar.current.dateComponents([.month, .day], from: birthday)
                    zodiacSign = calculateZodiacSign(birthday: birthdayComponents)
                    
                    // Show zodiac info if a sign is found
                    showZodiacInfo = zodiacSign != nil
                }
                .padding()
                
                // Show zodiac sign and provide options if a sign is found
                if let sign = zodiacSign {
                    Text("Your Zodiac Sign is \(sign.name)")
                        .font(.headline)
                        .padding()
                    
                    // Navigation links to different sections
                    NavigationLink(destination: ZodiacInfoView(zodiacSign: sign, infoType: "Compatibility")) {
                        Text("Compatibility")
                    }
                    .padding()
                    
                    NavigationLink(destination: ZodiacInfoView(zodiacSign: sign, infoType: "Element")) {
                        Text("Element")
                    }
                    .padding()
                    
                    NavigationLink(destination: ZodiacInfoView(zodiacSign: sign, infoType: "Qualities")) {
                        Text("Qualities")
                    }
                    .padding()
                }
            }
            .navigationBarTitle("Astrology App")
        }
    }
}

// Define a view to display information based on the selected zodiac sign and info type
struct ZodiacInfoView: View {
    let zodiacSign: ZodiacSign
    let infoType: String
    
    var body: some View {
        VStack {
            Text("\(infoType)")
                .font(.headline)
                .padding()
            
            // Display the appropriate information based on the info type
            if infoType == "Compatibility" {
                Text("Compatibility: \(zodiacSign.compatibility)")
                    .padding()
            } else if infoType == "Element" {
                Text("Element: \(zodiacSign.element)")
                    .padding()
            } else if infoType == "Qualities" {
                Text("Qualities: \(zodiacSign.qualities)")
                    .padding()
            }
        }
        .navigationBarTitle(infoType)
    }
}

// Define the main app
@main
struct AstrologyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}




