//
//  ContentView.swift
//  Astrology-CreateTask7th
//
//  Created by Brinda Morisetty on 4/11/24.
//
import SwiftUI

// Define the ZodiacSign struct to hold information about each zodiac sign
struct ZodiacSign {
    let name: String
    let startDate: DateComponents
    let endDate: DateComponents
    let element: String
    let qualities: String
}

// Define a list of zodiac signs with their respective date ranges, elements, and qualities
let zodiacSigns: [ZodiacSign] = [
    ZodiacSign(name: "Aquarius", startDate: DateComponents(month: 1, day: 20), endDate: DateComponents(month: 2, day: 18), element: "Air", qualities: "Innovative, Original"),
    ZodiacSign(name: "Pisces", startDate: DateComponents(month: 2, day: 19), endDate: DateComponents(month: 3, day: 20), element: "Water", qualities: "Compassionate, Intuitive"),
    ZodiacSign(name: "Aries", startDate: DateComponents(month: 3, day: 21), endDate: DateComponents(month: 4, day: 19), element: "Fire", qualities: "Confident, Courageous"),
    ZodiacSign(name: "Taurus", startDate: DateComponents(month: 4, day: 20), endDate: DateComponents(month: 5, day: 20), element: "Earth", qualities: "Reliable, Patient"),
    ZodiacSign(name: "Gemini", startDate: DateComponents(month: 5, day: 21), endDate: DateComponents(month: 6, day: 20), element: "Air", qualities: "Adaptable, Outgoing"),
    ZodiacSign(name: "Cancer", startDate: DateComponents(month: 6, day: 21), endDate: DateComponents(month: 7, day: 22), element: "Water", qualities: "Nurturing, Intuitive"),
    ZodiacSign(name: "Leo", startDate: DateComponents(month: 7, day: 23), endDate: DateComponents(month: 8, day: 22), element: "Fire", qualities: "Charismatic, Creative"),
    ZodiacSign(name: "Virgo", startDate: DateComponents(month: 8, day: 23), endDate: DateComponents(month: 9, day: 22), element: "Earth", qualities: "Detail-oriented, Analytical"),
    ZodiacSign(name: "Libra", startDate: DateComponents(month: 9, day: 23), endDate: DateComponents(month: 10, day: 22), element: "Air", qualities: "Diplomatic, Balanced"),
    ZodiacSign(name: "Scorpio", startDate: DateComponents(month: 10, day: 23), endDate: DateComponents(month: 11, day: 21), element: "Water", qualities: "Intense, Passionate"),
    ZodiacSign(name: "Sagittarius", startDate: DateComponents(month: 11, day: 22), endDate: DateComponents(month: 12, day: 21), element: "Fire", qualities: "Adventurous, Optimistic"),
    ZodiacSign(name: "Capricorn", startDate: DateComponents(month: 12, day: 22), endDate: DateComponents(month: 1, day: 19), element: "Earth", qualities: "Disciplined, Responsible")
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
                Text("Welcome to Astrology App")
                    .font(.largeTitle)
                    .padding()
                
                // Input for birthday
                DatePicker("Enter your birthday:", selection: $birthday, displayedComponents: [.date])
                    .datePickerStyle(WheelDatePickerStyle())
                    .padding()
                
                // Button to calculate zodiac sign
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
                    NavigationLink(destination: ZodiacInfoView(zodiacSign: sign, infoType: "Friendship Compatibility")) {
                        Text("Friendship Compatibility")
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
            if infoType == "Friendship Compatibility" {
                // For demonstration, display a fixed percentage
                Text("Friendship compatibility: 85%")
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
